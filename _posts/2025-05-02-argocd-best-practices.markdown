---
layout: post
title: 🚀 ArgoCD Best Practices for Scalable DevOps and MLOps Pipelines
date: 2025-05-02 12:00:00 +0000
description: GitOps Best Practices, ArgoCD best practices. # Add post description (optional)
img: argocd_h.png # Add image post (optional)
#fig-caption: Photo by <a href="https://unsplash.com/@jeshoots?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">JESHOOTS.COM</a> on <a href="https://unsplash.com/photos/woman-biting-pencil-while-sitting-on-chair-in-front-of-computer-during-daytime--2vD8lIhdnw?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
tags: [argocd, cicd, gitops, devops, mlops] # add tag

---

## Real-world tips to streamline your GitOps workflow, boost automation, and manage both app and ML deployments with confidence.

When you are working with Kubernetes and GitOps, ArgoCD is one of those tools that just come to your mind to help to implementation of GitOps methodology, making simple to automate, infrastructure as code, control, and application deployments, while keeping everything versioned and traceable using the version control like Git as the only source of true.

I’ve been working implementing GitOps methodologies using ArgoCD in several real-world environments from small automation labs to full-scale DevOps and MLOps platforms. Today I want to share a set of practical best practices that helped me streamline pipelines and avoid common mistakes. Whether you're just getting started or already deep into GitOps, there's something here for you. Let’s dive in! 🌊

---

## 1. 🗂️ Organise Your Git Repositories Smartly

Start by separating your application code from your deployment configuration:

- Keep **source code** in one repository
- Keep **manifests, Helm charts, or Kustomize overlays** in another
- Keep **infrastructure** related configuration in separate repository, even if that is related only to the same app project you are automating 
- Keep **images** in an image register or artifactory made for it.

This gives you better control, makes security audits easier, and avoids accidental changes in production environments.

It also allows you to reuse some infrastructure or software installation that are commonly used across teams.

If you're managing multiple environments (like `dev`, `stage`, `prod`), use **dedicated folders or branches** for each. It keeps things clean and allows ArgoCD to track changes precisely.

---

## 2. 🔄 Automate Syncing Wisely

Enable **auto-sync** to let ArgoCD apply changes as soon as they're committed to Git—but be cautious with production. In critical environments, you might want to pair auto-sync with **manual approvals**. 

You can set this up using a `webhook` that triggers the ArgoCD deployment after a pull request is approved and merged. Just configure one or more approvers to review and validate the PR before it goes through, especially for pre-prod and prod environments.

Also, take advantage of **sync hooks** (`PreSync`, `Sync`, `PostSync`) to handle setup tasks, database migrations, or health checks before and after deployment.

> ⚠️ Just a heads-up—if you want your source control **webhook** to trigger deployments, make sure **auto-sync** is enabled in ArgoCD.

---

## 3. 🔐 Control Access with RBAC

RBAC in ArgoCD is your friend—use it to define exactly **who can deploy, update, or delete** applications.

For CI/CD tools or other automation, create **dedicated service accounts** with the least privilege required. It’s a good security habit and helps prevent surprises.

In a cloud platform like Kubernetes, you can integrate with LDAP or AD to sync your groups and users, adding it to the ArgoCD instance controlled by the operator.
 
---

## 4. 💡 Use Health Checks and Sync Waves

Define **custom health checks**, especially if your app has multiple dependencies or needs a longer warm-up time. This helps ArgoCD decide whether a deployment was successful and if it needs to retry.

With **sync waves**, you can control the deployment order of different Kubernetes resources, which is really useful for microservices or apps with backend/frontend dependencies.

> ⚠️ Be careful—if your deployment includes lots of configuration, heavy resource provisioning, or services that take a while to start, your ArgoCD application might stay stuck in the *Processing* state for a long time (or even indefinitely). This is especially common when it's waiting on an external resource to become available or respond.



---

## 5. 🔁 Scale with Application Sets

Working with multiple clusters or teams? **ApplicationSets** can save your day.

* They allow you to manage multiple ArgoCD applications using templates. You can deploy to multiple clusters with similar configs without repeating yourself—true GitOps efficiency.

* You can also consider using Kustomize or Helm charts to handle different parameter values for your deployment.

* I prefer Kustomize when I have multiple configuration YAML files to apply via ArgoCD. It’s a great way to avoid creating Helm charts for everything, making things simpler and more manageable.



---

## 6. 🚦 Embrace Progressive Delivery

Gradual rollouts are a must in production. Tools like **Argo Rollouts** make it easy to implement **blue-green or canary deployments**.

Combine this with **auto-rollback** strategies in case something goes wrong. ArgoCD can detect issues and revert to a known-good state—peace of mind built-in.

---

## 7. 📊 Monitor and Audit Everything

Track what’s happening inside ArgoCD with **audit logs**—it’ll help you debug issues and track changes.

For real-time visibility, integrate monitoring tools like **Prometheus** and **Grafana** to alert you on sync failures, unhealthy apps, or performance issues.

---

## 8. 🔐 Lock Down Production Access

Always encrypt secrets—never store them in Git. Use Kubernetes Secrets, SealedSecrets, or a secrets manager like **Vault**.

You might also consider using Ansible Vault, especially if your policy isn’t too strict—this can work well for dev and test environments.
I’ve come across use cases where tools like HashiCorp Vault, CyberArk, and SealedSecrets were managed via ArgoCD, with their operators manifest, service account, and secrets integrated directly into the workflow.

Enable **Single Sign-On (SSO)** to manage access to ArgoCD securely and enforce limited access to production environments. 

✅ This is easy to set up when installing the ArgoCD operator on Kubernetes or similar platform, it automatically integrates with SSO, which can also be synced with LDAP or Active Directory.

---

## 9. ⚙️ Integrate with Your CI/CD Pipelines

ArgoCD works beautifully when integrated into CI/CD workflows. Configure your pipeline to:

- Push changes to Git
- Notify ArgoCD to deploy them

You can even automate **environment provisioning** (e.g., temporary review environments for PRs) using ArgoCD’s dynamic application management.

It doesn’t matter which CI tool you use—whether it’s TeamCity, Jenkins, Tekton, or something else—you need to ensure you have a proper test stage in place. Consider adding a stage to check the quality of your unit tests as well. After that, follow the usual stages, and don’t forget to include an image scan after the image is baked, but before it gets pushed to the registry or Artifactory.

You can add manual approval steps to your CI pipeline, or notify approvers when a new PR is created, allowing them to take the necessary actions. It all depends on your specific requirements.

---

## 10. 🛠️ Use Kustomize and Helm for Flexibility

I often use **Kustomize overlays** for fine-grained environment customisation without duplicating manifests.

For more parameterised deployments, **Helm** is a great fit—and ArgoCD supports it natively, especially when you're working with Kubernetes or a similar platform.

---

## 11. 🧭 Prioritise Observability and Logging

Route your app logs to a **centralised ELK stack** or similar. This helps you troubleshoot fast and ensures visibility across environments.

Don’t forget to monitor **resource usage** (CPU, memory, etc.) so you can right-size your clusters and apps as they grow.

It’s highly recommended to install ArgoCD on the cluster's infrastructure node, especially in a platform like Kubernetes. This helps avoid competing for resources with your applications and tools running on the worker nodes.

---

## 12. 🔄 Keep ArgoCD Updated and Reviewed

ArgoCD moves fast—make sure you **stay up to date** to benefit from the latest features, bug fixes, and security patches.

Also, take time every few weeks or months to **review your configs and RBAC policies** to ensure they still meet your team’s needs.

---

## 13. 🛡️ Plan for Disaster Recovery

Always have a **backup plan**. Back up both your Git repositories and your cluster state.

Because Git is your source of truth, if something goes wrong, ArgoCD can easily bring things back to life by syncing with your repository.

In the event of a data centre loss, I highly recommend automating your cluster installation and configuration with a tool like Ansible. You can create a custom Ansible collection to handle tasks like setting up cluster nodes, configuring security, syncing LDAP, installing ArgoCD with the proper RBAC, secrets, and certificates, and deploying the necessary ArgoCD application objects to sync with your repository. This way, you can restore everything quickly and without hassle.
  
---

## ⚠️ Extra Considerations 

In Kubernetes, it’s important to back up the operator manifest for disaster recovery. This includes the CRD installation, the ArgoCD instance, as well as the ConfigMap, service account, and secrets that allow your ArgoCD to SSH into your repository and registry. These backups ensure you can easily reinstall tools and redeploy your applications if needed.

Always test automation in Dev and Test environments first before applying it to Pre-Prod and Prod. Typically, organizations have these environments in different data centers, each with unique resource, storage, and domain requirements. This often means adjusting values files, Kustomize overlays, and other configurations accordingly.

## 🤖 Wait! What About MLOps? 

The same best practices we’ve covered above also apply when you're working with machine learning components, whether it's model deployment, model serving, serving registries, or ML pipeline workflows.

If you're running on a Kubernetes platform, these are typically just YAML configuration files. You can version them in your Git repository, and let ArgoCD treat that repo as the single source of truth, automating everything from model serving to pipeline execution, just like with regular application workloads.

👉 *I’ll walk you through a **real GitOps + MLOps example** in a future blog post, where we’ll dive deeper into how it all fits together in practice.* 😊



## 🧠 Final Thoughts

Following these best practices has helped me and my teams scale and secure our GitOps workflows across complex environments—from DevOps to MLOps. Whether you’re experimenting in your lab or managing production pipelines, ArgoCD can be a powerful ally.

Let’s keep learning, sharing, and improving together. 💪


>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


