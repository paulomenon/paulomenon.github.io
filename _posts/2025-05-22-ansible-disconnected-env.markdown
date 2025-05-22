---
layout: post
title: "Ansible in a disconnected environment"
date: 2025-05-22 12:00:00 +0000
description: "How to configure Ansible in a disconnected environment."
img: disconnected.jpg
fig-caption: 'Photo by <a href="https://unsplash.com/@davfts?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">David Pupăză</a> on <a href="https://unsplash.com/photos/text-heNwUmEtZzo?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>'
tags: [ansible, playbook, disconnected, devops, real-world]
---


# 🚫 How to Install Ansible in a Disconnected Environment

Have you ever found yourself needing to install Ansible in a completely disconnected environment?

No internet access, no `sudo` privileges, and stuck behind a proxy that blocks basic tools like `git clone`? To make things even trickier, you need a specific version of Ansible that isn’t available in any internal repositories—and the latest version just won’t cut it.  
In this blog, I’ll walk you through how I tackled this exact scenario on a Linux machine, and how you can too.

---

## 📦 Step 1: Download the Required Ansible Version

You can download compressed files such as `.zip` or `.tar.gz` from a Git repo.

The first step is to download the Ansible version you need from GitHub:

🔗 Go to [https://github.com/ansible/releases](https://github.com/ansible/releases)

Then find the version you want to install. For this example, I downloaded:  
**`ansible-core-2.14.15.tar.gz`**

📂 Unpack it to your preferred location — remember, you’ll need write permission there.

---

## 🧪 Note on Pyenv vs Virtualenv

> I tried using `pyenv` but that gave me too much trouble on the amount of work to get it to work because I needed to download the tar file from `pyenv` repo and the `pyenv-virtualenv` to install that plugin manually. Eventually, you need to set some environment variables to your `bash_profile` or similar.

I decided just to use **virtualenv** — it was already available to me.  
If it’s not available to you, you can install it with:

```bash
pip install virtualenv
```

🐍 Also, I already had Python 3.9 installed. If you need to install Python manually, you can check a guide online for that, as it’s required to run pip and for Ansible to work.

## ❓ Why Not Just Use pip install ansible?

I know what you're thinking — if Python is already installed and you can run pip commands, why not do:

```bash
pip install ansible
```
In this fiction but pratical scenario example, pip is pointing to an internal repository where I don’t have access to the specific Ansible version I need — which is 2.14.

🔧 Important: Ansible version 2.14 requires Python 3.

## 🛠️ Step 2: Set Up a Python Virtual Environment

Run this command to create a virtual environment using Python 3.9:

```bash
virtualenv -p /bin/python3.9 <your env name>
```

Activate the environment:

```bash
source <your env name>/bin/activate
```

## 📂 Step 3: Install Ansible from the Local Source

Go to the Ansible release root folder you unpacked earlier and run:

```bash
pip install .
```


## 🔁 Step 4: Make the Virtual Environment Persistent After Reboot

To ensure the virtual environment activates automatically (especially useful for VMs that reboot overnight), and run:

```bash
echo "source ~/virtualenvs/myenv/bin/activate" >> ~/.bash_profile
```

If you want that to also be ready when you open a new terminal or tab then using .bashrc, simply change the end of the command to:

```bash
echo "source ~/virtualenvs/myenv/bin/activate" >> ~/.bashrc
```

---

## 🛠️ Running Ansible Without Ansible Automation Platform

This scenario also covers cases where you don’t have access to a platform like **Ansible Automation Platform**, which normally provides the right execution environment and configuration for running playbooks and collections.

⚙️ It’s useful when:
- You need to test or develop locally
- You don’t have access to the full platform
- You want to check if your play works before run in a platform
- 

---

✅ **Hope this helps — see you next time!** 👋



>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


