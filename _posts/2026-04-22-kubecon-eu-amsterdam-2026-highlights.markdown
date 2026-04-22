---
layout: single
title: "KubeCon EU Amsterdam 2026 — My Highlights and Takeaways"
date: 2026-04-22 13:00:00 +0000
last_modified_at: 2026-04-22
description: "A comprehensive recap of KubeCon + CloudNativeCon Europe 2026 in Amsterdam — from keynote highlights and vendor announcements to hands-on labs, open-source project donations, and the people that make it all worthwhile."
tags: [kubecon, kubernetes, cloud native, cncf, ai, mlops, red hat, openshift, platform engineering, agentic ai, llm-d, amsterdam, conference]
header:
  og_image: "/assets/images/kubecon1.jpg"
---

## KubeCon EU Amsterdam 2026 — My Highlights and Takeaways

![KubeCon EU 2026 Welcome](/assets/images/kubeconwelcome2026.1.jpg)


I've been to two KubeCons now, both working the Red Hat booth as part of the **AI Pod** — running demos, answering questions, and supporting hands-on labs. Each time, I walk away feeling like the entire cloud-native conversation has shifted beneath my feet. Amsterdam was no different.

KubeCon EU 2024 in Paris — which I missed — surfaced the early tension between AI and Kubernetes. London 2025, my first, was all about infrastructure, with strong interest in running AI on Kubernetes and building MLOps pipelines. Amsterdam 2026 felt like the moment the industry stopped asking "can we run LLMs on Kubernetes?" and started asking the harder question: "how do we build intelligent, self-healing platforms that handle the massive scale of agentic AI — while keeping security, cost, and sovereignty under control?"

That shift — from experiment to operating model — was the thread running through every keynote, every booth conversation, and every hallway debate.

![At the Red Hat booth](/assets/images/kubecon2.jpg)

Here is my wrap-up of **KubeCon + CloudNativeCon Europe 2026**.

---

## By the Numbers

| KPI | 2026 Statistic | Trend (vs 2025) |
|---|---|---|
| Total Attendees | 16,500+ | +10% |
| In-Person Attendees | 14,000+ | +15% |
| Participating Organisations | 2,800+ | Up |
| Total CNCF Projects | 210+ | Up |
| CFP Submissions | 3,500+ | Record High |
| Acceptance Rate | ~11% | Most Competitive |

The numbers speak for themselves. With an 11% acceptance rate, the bar for getting a talk accepted is now absurdly high — which means the session quality reflects it.

---

## Keynotes — From Experimentation to Execution

The keynotes cemented what many of us have felt for a while: Kubernetes is no longer the main character. It has become the invisible engine powering the intelligence age. CNCF leadership and industry pioneers made it clear — we have moved from **AI experimentation to production execution**.

Two themes dominated the stage:

**Digital Sovereignty by Design** — The impending EU Cyber Resilience Act (CRA), effective September 2026, has turned compliance from a checkbox into an architectural requirement. **Greg Kroah-Hartman** stressed that open-source sustainability and compliance must be baked into the stack, not bolted on. For anyone building platforms in Europe, this is no longer optional.

**Invisible Kubernetes** — AWS's **Jesse Butler** showcased how projects like **Karpenter**, **kro**, and **Cedar** are abstracting cluster complexity to the point where engineers shouldn't need to think about Kubernetes at all. The message across the board: GPU scheduling is standardising, agentic AI needs strict governance, and the era of artisanal cluster management is over.

![Keynote stage](/assets/images/kubecon3.jpg)

The sovereignty conversation went deeper during **Vincent Caldeira's** keynote — true sovereignty means controlling your organisation's digital destiny, not just data residency. On Day 2, an excellent **theCUBE** interview with Caldeira and **Roberto Carratalá** mapped out what this looks like in practice: platform teams serving data scientists, validated model catalogues, trust through SBOMs, and standards like **llm-d** to squeeze more out of expensive GPU infrastructure.

🎥 **Watch the full interview here:** [theCUBE — Vincent Caldeira & Roberto Carratalá](https://www.youtube.com/watch?v=-4foKbCVYy4)

---

## On the Show Floor

I love working the booth. I love talking to people, representing the engineers I work with, meeting new faces, and catching up with old friends — sometimes KubeCon is the only chance to see them in person. The marketing team gave us everything we needed to deliver a great experience, and the energy from visitors was fantastic.

Between booth shifts, I explored the sponsor hall. Here is what stood out — from Red Hat and beyond.

![Sponsor hall highlights](/assets/images/kubecon4.jpg)

---

### Red Hat — Where I Spent Most of My Time

![KubeCon EU 2026](/assets/images/myself_kubecon2026.1.jpg)

Red Hat's booth was one of the most interactive on the floor, organised around dedicated pods that let people go deep rather than skim the surface.

- **Hands-On Labs** — Engineers queued up to get keyboard time with **Event-Driven Ansible**, **GitOps with ArgoCD**, and **Podman on OpenShift**. These weren't demos to watch — they were real labs to work through, and the engagement showed.

- **OpenShift AI Pod** — This was where I spent most of my time. We ran a full **GenAI Studio** demo with MCP server integration, showed the new **llm-d** project for disaggregated serving, and walked people through the **model catalogue** and **Model-as-a-Service** capabilities. The questions we got were sharp — people aren't experimenting anymore, they're planning production rollouts.

- **OpenShift Virtualisation Pod** — VM modernisation is still a massive enterprise priority, and the dedicated **KubeVirt** pod showed how to orchestrate legacy VMs alongside containers on a single platform. This resonated strongly with operations teams.

- **Rotating Pods** — Platform Engineering and Security rotated daily, with deep technical discussions that drew consistent crowds throughout the week.

I also want to call out a hands on lab session I unfortunately couldn't attend but heard outstanding feedback about.

![Hands-on labs](/assets/images/kubecon5.jpg)

**Building Intelligent Apps with RAG** — Led by **Natale Vinto** alongside **Cedric Clyburn**, **Christopher Nuland**, and **Legare Kerrison**, this packed tutorial walked attendees through deploying production-ready Retrieval-Augmented Generation on a cloud-native stack. Natale also did book signings and media interviews on the floor, making a point I completely agree with: AI adoption is ultimately a process challenge, not just a technical one.

![Cedric massive help](/assets/images/kubecon5.1.jpg)

---

### Red Hat Presenters Helping at the Booth

![Presenter and booth staff](/assets/images/kubecon_andy.jpg)

KubeCon had a wealth of presentations and breakout sessions worth attending. It's always great that our Red Hat presenters also help us at the booth — we had a lot of them, but I just want to highlight **Andy Block**, who participated in several sessions such as [Helm 4 Is Here. So Now What?](https://www.redhat.com/en/events/red-hat-kubecon-cloudnativecon-europe-2026) and [ModelPack: Standardizing the Packaging and Distribution of AI/ML Models](https://cloudsmith.com/blog/13-kubecon-europe-2026-sessions-not-to-miss). He also did a book signing for his book **Argo CD Up and Running**, and helped us on the Security Pod explaining everything in our Trust portfolio with **Advanced Cluster Security**.

---

### What Caught My Eye from Other Vendors

![Vendor highlights](/assets/images/kubecon6.jpg)

Rather than listing every announcement, here are the ones that actually matter for engineers building platforms today:

**The convergence around llm-d** — **Google**, **IBM**, and **Red Hat** all backed **llm-d** as the standard for disaggregated inference serving, separating prefill and decode phases across pods. When three major players align on the same open standard, pay attention — this will likely become the default pattern for efficient LLM serving on Kubernetes.

**Solo.io's kagent** — This was the most interesting thing I saw outside the Red Hat booth. **kagent** defines AI agents as Kubernetes CRDs with pre-built MCP servers, making agents first-class, observable, RBAC-governed resources. If you're thinking about running agentic workloads on Kubernetes, this project is worth watching closely.

**AWS SOCI Parallel Pull** — A practical win for anyone running large AI containers. By parallelising image download and unpacking, AWS demonstrated nearly **60% faster startup** for containers with massive model files. Combined with **Karpenter** improvements for GPU access, AWS is clearly investing in making AI workloads feel native on EKS.

**Microsoft AI Runway** — An open-source Kubernetes API for inference that handles Hugging Face model discovery, GPU memory fit calculations, and cost estimates. Useful if you need a quick way to evaluate whether a model fits your cluster's resources before deploying.

**Security: policy-as-code from day one** — Both **Palo Alto** (with Prisma AIRS) and **Wiz** drove home the same message: retrofitting identity and security onto an agent fleet after the fact is painful. The consensus was clear — if you're building agentic platforms, embed policy-as-code from the start.

---

## Ecosystem Updates Worth Noting

**Portworx** — Focused on AI/HPC storage performance with **FlashBlade//EXA** and **Portworx Backup** for protecting stateful AI workloads like model weights and checkpoints.

**HashiCorp** — **Vault** is becoming increasingly Kubernetes-native through sidecar secrets injection and the **Terraform Operator for Kubernetes**. If you're already in the HashiCorp ecosystem, the integration story keeps getting tighter.

**Grafana Labs** — Pushed the idea of monitoring-as-code for AI applications, with new semantic conventions for instrumenting generative AI workloads across **Prometheus**, **Tempo**, and **Grafana** dashboards.

---

## CNCF Sandbox Donations — The Ones to Watch

<p align="center">
  <a href="https://www.cncf.io/"><img src="/assets/images/cncf-color.png" alt="CNCF Logo" width="300"></a>
</p>

The projects entering the [CNCF](https://www.cncf.io/) Sandbox this year are solving real production bottlenecks, not just filling whitespace:

- **<i class="fab fa-github"></i> [llm-d](https://github.com/llm-d/llm-d) (IBM/Red Hat/Google)** — Standardising disaggregated inference serving. Given the backing, this has a real shot at becoming the default.
- **<i class="fab fa-github"></i> [KAI Scheduler](https://github.com/NVIDIA/KAI-Scheduler) (NVIDIA)** — A GPU-aware scheduler for intelligent workload placement. If you're fighting with GPU bin-packing today, keep an eye on this.
- **<i class="fab fa-github"></i> [kagenti](https://github.com/kagenti/kagenti) (IBM)** — Cryptographic identities for AI agents using SPIFFE/SPIRE. Agent identity is a hard, unsolved problem — this is a serious attempt at fixing it.
- **<i class="fab fa-github"></i> [Velero](https://velero.io/) (Broadcom)** — The beloved backup tool moved into the Sandbox, which matters more now that AI workloads are increasingly stateful.

---

## The Swag and Books

The Red Hat swag was a massive hit as usual, with loads of people asking for it — which finished in less than an hour, sending a nice wave of people wearing our beloved brand all over the conference.

![Swags](/assets/images/kubecon7.jpg)

No KubeCon is complete without the swag, and Amsterdam delivered. The official T-shirt design was great — similar style to London's, with a Netherlands twist. The sticker walls were mobbed as usual, and Red Hat's own sticker wall was a crowd favourite — second only to the Red Hat hat giveaway, which disappeared almost instantly.

### The Best Swag is Knowledge

But the real prizes were the book giveaways. Several booths hosted signings and drops, and the queues were long.

![My book haul from KubeCon](/assets/images/kubecon7.1.jpg)

I managed to grab **[Generative AI on Kubernetes](https://www.oreilly.com/library/view/generative-ai-on/9781098171919/)**, **[Argo CD Up and Running](https://www.amazon.com/Argo-CD-Running-Hands-Kubernetes/dp/1098142004)**, and **[Modernizing Enterprise Java](https://www.amazon.com/Modernizing-Enterprise-Java-Concise-Developers/dp/1098102142)**. Amidst all the talk of LLMs and autonomous infrastructure, there's something grounding about having a solid reference book on your desk to help you actually build the things we spent all week discussing.

📚 Don't forget to grab your copy — check out the links above!

![Best books in  KubeCon](/assets/images/kubecon7.2.jpg)

---

## A Special Highlight — Meeting TechWorld with Nana

One of the personal highlights of the event was meeting **Nana Janashia**, the creator of **TechWorld with Nana**. I had the chance to tell her that my colleagues and I regularly recommend her channel — not just for our own learning, but as a go-to resource for new talent and engineers advancing their careers within Red Hat. It was great to personally thank someone who has done so much to make DevOps and Kubernetes accessible to everyone.

![Meeting Nana Janashia from TechWorld with Nana](/assets/images/kubecon9_nana.jpg)

<i class="fab fa-youtube"></i> **Check out her channel:** [TechWorld with Nana](https://www.youtube.com/results?search_query=nana+techworld)

---

## Moving Past the Hype

KubeCon EU 2026 was a maturing moment. AI provided the spark, but the real conversation was about engineering — how to build these systems reliably, securely, and at scale.

That said, AI saturation was real. The meme that KubeCon has become "AICon" made the rounds, and it wasn't entirely wrong. Whether that sticks remains to be seen.

But beyond the tech, the most important part of KubeCon for me is always the people. Reconnecting with friends and colleagues, sharing honest insights about the projects we're building, meeting customers, and talking to enthusiastic engineers who want to join us — that's what makes the trip worthwhile.

I'm always reminded of a friend who joined Red Hat after being inspired by our booth at KubeCon three years ago. I hope that "KubeCon magic" keeps sparking conversations and drawing more people into the open-source community.

I won't be at KubeCon NA in Salt Lake City later this year, but I'm keen to see how these intelligent platforms handle their first production-scale agentic workloads.

The next KubeCon EU events have been announced — **[KubeCon Barcelona in 2027](https://events.linuxfoundation.org/kubecon-cloudnativecon-europe-2027/)** and **[KubeCon Berlin in 2028](https://events.linuxfoundation.org/kubecon-cloudnativecon-europe-2028/)**. I'm not sure yet if I'll be there, but I really hope so. Start making your plans, and let's hope to see you there! ;)
