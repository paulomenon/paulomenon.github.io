---
layout: post
title: "DevOps Automation Reusability"
date: 2025-06-26 12:00:00 +0000
description: "Ansible collections explained and examples"
img: ansible_collection.png
#fig-caption: 'Photo by <a href="https://unsplash.com/@davfts?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">David Pupăză</a> on <a href="https://unsplash.com/photos/text-heNwUmEtZzo?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>'
tags: [ansible, ansible galaxy, ansible collection,playbook, disconnected, devops, real-world]

---

## Ansible collections explained: Why reusability is important in automation

If you aren’t familiar with or haven’t been using Ansible collections as much, this is a brief explanation of what an collection is.

Ansible collections are designed to help organise and reuse automation content more efficiently, especially in large enterprise environments.

They help you create more modular reusable content, making it easier to share across projects or teams. Collections also simplify installation, are versioned independently, enabling isolated updates, and track compatibility and dependencies.

You probably already use some of the Ansible collections available in the Automation Hub provided by Red Hat or partners, which offers a collection of certified, supported, and security-tested content. Alternatively, a custom collection that you create yourself will be specific to your organisation's needs, tools, and processes, giving you full lifecycle control over it.

To install a collection or create your own, you need to use `ansible-galaxy`, which comes with the installation of Ansible.

## Ansible Collections

As exmplained before `Collections` are a way to package and distribute reusable Ansible content, such as roles, modules, plugins, and documentation.
You can also create your collection, which can include playbooks, roles, modules, templates, variables, and plugins.

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy collection init my_namespace.my_collection
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

Your folder structure will look like this

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
my_collection/
├── README.md
├── galaxy.yml
├── plugins/
│   ├── module_utils/
│   └── modules/
            ├── roles/
│   └── my_role/
│       ├── tasks/
│       │   └── main.yml
│       └── README.md
└── docs/

{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

#### Ansible Roles

Organize your playbooks and tasks into reusable components called roles. Learn how to structure and use roles across multiple playbooks.

A **role in Ansible** is a way to organize tasks, variables, files, and templates for reuse across playbooks. It encapsulates specific functionality or configurations, making your automation code modular and easier to manage.

#### Ansible Modules

**Modules** are small units of code that Ansible uses to perform tasks on managed hosts.

Get familiar with **Ansible modules**, which are reusable units of code for executing tasks on managed nodes. Explore the wide range of built-in modules for operations like file manipulation, package management, and service management.

#### Using Ansible Inventories

Execute your playbooks against the inventory of hosts using the ansible-playbook command.

Understand options like limiting the hosts, specifying the inventory file, and verbose output.

To execute an Ansible playbook with specific options, use the ansible-playbook command. Here's an example:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-playbook myplaybook.yml -i inventory.yaml --limit webservers --verbose
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

* **myplaybook.yml:** The playbook file to run.
* **-i inventory.yaml:** Specifies the inventory file.
* **--limit webservers:** Limits execution to hosts in the webservers group.
* **--verbose:** Provides detailed output during execution.

#### Ansible Handlers

Learn about **handlers**, and tasks triggered by other tasks when changes occur.

Understand how to define and use handlers to restart services or perform other actions only when necessary.

Let’s say for example you need to run an Ansible playbook to change the apache.conf on your Apache server then you want to guarantee that the server gets restarted. Your handler can be implemented to restart Apache every time that configuration is modified. 

In your role directory structure, you might have:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
roles/
└── webserver/
    ├── tasks/
    │   └── main.yml
    └── handlers/
        └── main.yml

{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

You might have a task to manage the Apache configuration file:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
---
- name: Ensure Apache configuration file is present
  template:
    src: apache.conf.j2
    dest: /etc/apache2/apache.conf
  notify: Restart Apache
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

You implement the handler like this:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
---
- name: Restart Apache
  service:
    name: apache2
    state: restarted
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

#### Ansible Galaxy

Ansible Galaxy is a community platform for sharing and downloading Ansible content, including **roles** and **collections**. It allows users to find pre-built automation components to speed up their playbook development, promoting reuse and collaboration across projects.

**Collections** function like plugins you can install in Ansible, enabling the use of native modules to execute tasks directly, rather than relying on shell command wrappers.

Using an **Ansible collection** instead of wrapping commands in shell tasks provides better maintainability, readability, and idempotence. Collections offer reusable modules tailored for specific tasks, reducing the risk of errors and ensuring consistent execution, while shell commands are harder to debug and may not be idempotent.

You can find asible community colleciton in [here](https://docs.ansible.com/ansible/latest/collections/index.html) 

You also can create your own following this steps [here](https://docs.ansible.com/ansible/latest/dev_guide/developing_collections.html)

You can verify the installation by running:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy collection list
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

For example if you want to install kubernetes core collection, use the following command:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy collection install community.kubernetes
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

**Explanation:**

- community.kubernetes is the namespace and collection name for k8s.core.

- This command downloads and installs the collection to your local Ansible environment, making its modules and plugins available for use in your playbooks.

# Tutorial

### Installing Collections Examples

For example, if you want to automate tasks related to Kubernetes, you can install the `kubernetes.core` collection as follows:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy collection install kubernetes.core:<specific_version>
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

If you need to automate tasks on an IBM mainframe, you can use this collection:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy collection install ibm.zos
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

## Creating Your Own Collection

Now, let’s create our collection and understand the folder structure within:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy collection init pamenon_org.gitops
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

Folder structure:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
pamenon_org-gitops/
├── plugins/
├── roles/
├── playbooks/
├── galaxy.yml
└── README.md

{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

- Namespace `(pamenon_org)`: This is like your organisation or user name. It groups collections logically and avoids name clashes with others. Think of it as your “brand” or “owner” of the collection.

- Collection Name `(gitops)`: The specific collection’s name within your namespace. It describes what the collection does — here, automation related to GitOps.

## Directory Structure inside pamenon_org-gitops/

`plugins/:` Contains custom Ansible plugins like modules, filters, callbacks, or connection plugins you write and include in the collection.

`roles/:` Contains Ansible roles, which are reusable, modular sets of tasks for specific automation purposes (e.g., deploying apps, configuring servers).

`playbooks/:` An optional folder to include example or helper playbooks that use your roles or plugins.

`galaxy.yml:` Metadata file describing your collection (name, version, dependencies, author, etc.) — used when publishing or installing the collection.

`README.md:` Documentation file to explain what your collection does, how to use it, etc.

## Creating Roles in Your Collection

Roles contain modular sets with their own tasks, variables, and templates.

Create two roles for the gitops collection like this:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
cd pamenon_org.gitops
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy role init roles/argocd
ansible-galaxy role init roles/openshift_infra

{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

## Folder structure example:

<img src="../assets/img/folder_structure.png"  width="600" height="700"  title="folder structure example" >


## Creating a Shared Security Role

You can create another role that will be shared between the other two roles for access and authorization called `security`.

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
ansible-galaxy role init roles/security
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

## Role Design Plan

### 🔐 security role

Handles authentication and access setup.

### Responsibilities:

- oc login (auth to OpenShift)

- Set up SSH keys for Git repo access

- Export kubeconfig or credentials

- Create any common secrets/certs used by other roles

### 🚀 argocd role

Depends on security for login and access.

### Responsibilities:

- Install Argo CD (e.g., with oc apply, Helm, or Operator)

- Configure Argo CD CLI or custom resources

- Set up Git repo access (private key, repo URL)

- Sync applications if needed


### 🏗️ openshift_infra role

Also depends on security.


### Responsibilities:

- Create service accounts

- Set network policies

- Install internal certificates

- Create secrets for apps or services

## ✅ Conclusion

Ansible Collections are a powerful way to structure, share, and scale your automation efforts. By embracing collections, you gain better modularity, version control, and reusability—essential for managing complex, enterprise-scale environments. Whether you're using certified content from Ansible Galaxy or building custom collections tailored to your needs, this approach helps streamline collaboration, improve maintainability, and ensure consistent automation practices.

I hope you found this guide helpful—thanks for reading, and see you next time! 👋



>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


