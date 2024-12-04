---
layout: post
title: Getting started with Ansible - Your learning path guide.
date: 2024-12-04 12:00:00 +0000
description: Kickstart your ansible journey with key concepts and basic examples. # Add post description (optional)
img: ansible.jpg # Add image post (optional)
#fig-caption: Photo by <a href="https://unsplash.com/@jeshoots?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">JESHOOTS.COM</a> on <a href="https://unsplash.com/photos/woman-biting-pencil-while-sitting-on-chair-in-front-of-computer-during-daytime--2vD8lIhdnw?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
tags: [Ansible, GettingStartedWithAnsible, LearnToAutomate,AutomationTools] # add tag

---

## Introduction ✨

I've put together a learning path that significantly helped me improve my automation skills, and I believe it can do the same for you! 🚀

So, how does this work for you if you're just starting out, whether you're fresh out of university 🎓, switching careers 🔄, or have basic (or no) knowledge of the **tools** around **automation**? 🤖

In that case, I highly recommend starting with the **prerequisites** first. 🛠️ You’ll need to get familiar with the tools you’ll be using and the systems you’ll be automating to lay a strong foundation before diving into Ansible.

On the other hand, if you're like me and come from a different IT background—whether it's programming 💻, infrastructure administration 🖧, cloud administration ☁️, or something else—you can **skip the prerequisites** and jump straight into the core content. 

This path is designed to get you up to speed and enhance your automation skills, no matter where you're starting from! 🌟


## Prerequirements

<button class="collapsible-btn" onclick="toggleContent()">Close Prerequirements</button>

<div class="collapsible-content">
This section is specifically for those who don’t have any background in Linux administration, Windows administration, cloud administration, or programming. 

If you’re new to these areas, it's important to first build a foundational understanding of the basic concepts and tools that you'll be automating with Ansible.

By getting familiar with these fundamentals, you'll be better equipped to dive into automation and take full advantage of what Ansible has to offer.

To get started, you'll need to familiarize yourself with a few key concepts, CLI tools, scripting languages, and some basic knowledge of configuration, networking, and cloud management. 

These are essential because you'll be using Ansible to automate those tasks.

You don’t need to dive deep into all the videos—just enough to get comfortable with the tools and concepts you'll be automating. 

This will give you a solid foundation as you move forward with Ansible and automation.

<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    padding: 10px;
    text-align: left;
    border: 1px solid #ddd;
    
  }
  th {
    background-color: #325463
  }
  tr:nth-child(odd) {
    background-color: #f2f2f2; /* Light grey for odd rows */
  }
  tr:nth-child(even) {
    background-color: #e6f7ff; /* Light blue for even rows */
  }
</style>

<table>
  <thead>
    <tr>
      <th>Skills</th>
      <th>Descriptions</th>
      <th>Links</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Basic Linux knowledge</b></td>
      <td>Useful Linux command lines to get you started</td>
      <td><a href="https://www.youtube.com/watch?v=gd7BXuUQ91w&t=4s&ab_channel=NetworkChuck" target="_blank">NetworkChuck</a></td>
    </tr>
   <tr>
      <td><b>Networking skills</b></td>
      <td>Understanding basic networking and setups</td>
      <td><a href="https://www.youtube.com/watch?v=keeqnciDVOo&ab_channel=Fireship" target="_blank">Learn Networking Fundamental</a></td>
    </tr>
     <tr>
      <td><b>Comfortable using the command line interface</b></td>
      <td>Introduction to command line usage</td>
      <td><a href="https://www.youtube.com/watch?v=Q1dwzi5DKio&ab_channel=Techquickie" target="_blank">Why Do Command Line Still Exist?</a></td>
    </tr>
    <tr>
      <td></td>
      <td><b>Beginner’s Linux terminal tutorial</b></td>
      <td><a href="https://www.youtube.com/watch?v=s3ii48qYBxA&ab_channel=DistroTube" target="_blank">Begginer’s Linux terminal tutorial</a></td>
    </tr>
    <tr>
      <td><b>Version control tools</b></td>
      <td>Git for beginners</td>
      <td><a href="https://www.youtube.com/watch?v=8JJ101D3knE&ab_channel=ProgrammingwithMosh" target="_blank">Git for beginners</a></td>
    </tr>
    <tr>
      <td></td>
      <td><b>How to use git basic commands</b></td>
      <td><a href="https://www.youtube.com/watch?v=2ldhr1vQtoI&ab_channel=TonyTeachesTech" target="_blank">How to use git basic commands</a></td>
    </tr>
    <tr>
      <td><b>Familiarity with YAML syntax</b></td>
      <td>Learn YAML syntax basics</td>
      <td><a href="https://www.youtube.com/watch?v=BEki_rsWu4E&ab_channel=KahanDataSolutions" target="_blank">Yaml tutorial</a></td>
    </tr>
    <tr>
      <td></td>
      <td><b>Check YAML format</b></td>
      <td><a href="https://jsonformatter.org/yaml-formatter" target="_blank">Yaml format check</a></td>
    </tr>
    <tr>
      <td><b>Understanding of IT infrastructure concepts</b></td>
      <td>Learn Ansible and network configuration concepts</td>
      <td><a href="https://www.youtube.com/watch?v=SJtRh1B0FxY&ab_channel=RedHat" target="_blank">Asible to configure your network connection concepts</a></td>
    </tr>
    <tr>
      <td><b>Basic scripting</b></td>
      <td>Learn Bash scripting basics</td>
      <td><a href="https://www.youtube.com/watch?v=I4EWvMFj37g&ab_channel=Fireship" target="_blank">Bash Script basic</a></td>
    </tr>
    <tr>
      <td></td>
      <td><b>Learn shell scripting basics</b></td>
      <td><a href="https://www.youtube.com/watch?v=Iaehl5df_6I&list=PLlr7wO747mNrtDMzJ3IpNuttDxSoKp9TB&ab_channel=DexTutor" target="_blank">Shell Script tutorial</a></td>
    </tr>
    <tr>
      <td><b>SSH Keys</b></td>
      <td>Learn SSH basics</td>
      <td><a href="https://www.youtube.com/watch?v=v45p_kJV9i4&ab_channel=CodeWithBubb" target="_blank">SSH Basics in 6 min</a></td>
    </tr>
    <tr>
      <td></td>
      <td><b>Ansible SSH basics</b></td>
      <td><a href="https://www.youtube.com/watch?v=-Q4T9wLsvOQ&list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70&index=3&ab_channel=LearnLinuxTV" target="_blank">Ansible SSH Foundation</a></td>
    </tr>
    <tr>
      <td><b>Understanding of virtualization and cloud computing basics</b></td>
      <td>Learn the difference between VMs and Containers</td>
      <td><a href="https://www.youtube.com/watch?v=a1M_thDTqmU&ab_channel=IBMTechnology" target="_blank">VMs vs Containers</a></td>
    </tr>
    <tr>
      <td><b>Using IDE to implement your automation</b></td>
      <td>Learn how to use VSCode with Ansible</td>
      <td><a href="https://www.youtube.com/watch?v=iI6cSvL87xY&ab_channel=AlexDworjan" target="_blank">VSCode with Ansible</a></td>
    </tr>
  </tbody>
</table>

<br>
Have you done your prerequirments and go back here so head to next section and dig in some anible.


</div>
 <script>
    // Function to toggle the visibility of the collapsible content
    function toggleContent() {
      var content = document.querySelector(".collapsible-content");
      content.style.display = content.style.display === "none" || content.style.display === "" ? "block" : "none";
    }
  </script>

## Ansible Understanding the Basics:

### What is Ansible? 🤔

**Ansible** is a powerful tool that helps automate a wide range of **IT tasks**, such as **configuring networks**, **installing software**, **setting up servers** and **cloud infrastructure**, **managing configurations**, **sending and receiving messages**, and **more**.

It uses a simple **YAML format** text file to define tasks and connects to target machines using **SSH** — **no additional software or agents are required**. Built on top of **Python**, **Ansible** leverages Python’s capabilities, meaning it can accomplish anything that Python can. What makes Ansible especially popular is that it doesn’t require you to be a Python programmer, and it’s incredibly easy to use.

This video will provide you with an introduction to Ansible, helping you understand its core concepts and getting you started on your learning path.

<a href="https://www.youtube.com/watch?v=1id6ERvfozo&list=PLy7NrYWoggjxKDRWLqkd4Kbt84XEerHhB&ab_channel=TechWorldwithNana" target="_blank">Ansible Tutorial - What is Ansible with TechWorldWithNana</a>


### infrastructure as code (IaC) 🛠️

Familiarize yourself with the concepts of configuration management and **infrastructure as code (IaC)**.

Configuration management refers to the process of handling and maintaining consistent software configurations across systems, while Infrastructure as Code is the practice of managing and provisioning IT infrastructure through code rather than manual processes.

### Ansible’s architecture 🏗️

Next, dive into **Ansible’s architecture**. 

**Ansible** operates with a control node (the machine running Ansible commands), managed nodes (the machines being configured or automated), and inventory (the list of managed nodes). Understanding how these components work together is key to leveraging Ansible’s full potential.

After the installation section, let’s go over some key points to solidify your understanding.

### Installation 💾

Install Ansible on your local machine or a control node. Ansible can be installed on Linux, macOS, or Windows.

Follow the official  for your operating system. 

You can follow the official <a href="https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html" target="_blank">Ansible installation Guide</a> for your operating system. Below are the installation commands for Red Hat Enterprise Linux (RHEL) and macOS

- RHEL:
<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
sudo dnf install ansible
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

- MacOS
<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
brew install ansible
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

Are you on Mac? but you don’t have **homebrew** yet? then go get  <a href="https://brew.sh/" target="_blank">brew here</a>.🍺

### Ansible Key Concepts 🗝️

Before you start coding with Ansible, make sure to review these key concepts.

#### Where does Ansible run? 🏃‍♂️💻

Ansible runs on the control host and uses SSH to communicate with target hosts, performing tasks and applying configurations.

#### Ansible Control Host 🖥️🎮

The Ansible control host is the machine where Ansible is installed, and from which you run Ansible commands and playbooks.

#### Ansible Target Hosts 🎯💻

Target **hosts**, or **managed nodes**, are the machines that Ansible manages and configures.

#### Ansible Playbook ▶️📚

An **Ansible playbook** is a YAML file that outlines the tasks Ansible will execute on managed systems in a specific order. It defines steps to configure servers, deploy applications, or install software on cloud platforms.

Here a **hello world ansible playbook** example:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
---
- name: Hello World Playbook
  hosts: all
  tasks:
    - name: Print Hello World
      ansible.builtin.debug:
        msg: "Hello, World!"
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

#### Ansible Inventory 📋🔧

In Ansible, the **inventory** defines the hosts where tasks will be executed.

You can create a simple inventory file with one or more hosts and groups.

Open your preferred text editor (I use VSCode) and create a file like this:

<div class="code-snippet">
  <div class="highlight">
{% highlight command-line %}
[webservers]
web1.example.com
web2.example.com

[webservers:vars]
ansible_user=webadmin
ansible_python_interpreter=/usr/bin/python3

[databases]
db1.example.com
db2.example.com

[databases:vars]
ansible_user=dbadmin
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

## Conclusion 🚀

Embarking on your Ansible journey can be both exciting and rewarding. By following the outlined learning path, you'll gain a solid understanding of automation, empowering you to streamline IT tasks and manage complex environments efficiently. Whether you're building foundational skills or expanding your existing expertise, Ansible provides a versatile toolkit to transform your workflow. ⚙️💻

Remember, mastery comes with practice. Start small, experiment with playbooks, and gradually tackle more advanced scenarios. The automation landscape evolves rapidly, so keep exploring, stay curious, and share your insights with the community. 🌟 Happy automating! 🎉 See you next time with more! 🚀✨


>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


