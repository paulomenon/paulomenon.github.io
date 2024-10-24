---
layout: post
title: Install multiple JDKs on your Mac.
date: 2024-10-24 12:00:00 +0000
description: Install multiple JDKs in your local environemnt. # Add post description (optional)
img: java_coffee.jpg # Add image post (optional)
tags: [ProgrammingForBeginners, LearnToCode,TechCareer,  CodingTips, Programming, ProblemSolving, Python] # add tag

---
# Install multiple JDKs in your on Mac.

I will cover in this blog how to install multiple JDK on Mac, but you can do a similar process in Linux or Windows.

# Why do you need to have multiple JDKs anyway? 

If you need to test the Java application with different JDK compilers or if you like me a consultant who needs to assist several different customers with different setups and you want to have a flexible way to switch from one version to another.

It’s also useful if you need to do an app modernization project looking into moving from old JDK versions to the newest.

Let’s get started.

# Install Java

I will guide you in a few steps on how to install Java, if you on Linux you can use your own package manager tool like Yum, dnf, etc.

First, if you are on Mac you should consider using Homebrew or any other package manager tool to make your life easy to install anything you need to program from Java to Python.

# Homebrew
Get https://brew.sh/[Homebrew].

Now that you have it, you can run the following command.

<div class="code-snippet">
  <div class="highlight">
{% highlight command %}
brew search openjdk
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
 </div>
</div>

The output should be something like this.

![image](../assets/img/brew_search.png)

Choose the JDK version you want to install and type this.

<div class="code-snippet">
  <div class="highlight">
{% highlight command %}
brew info --cask adoptopenjdk8
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
 </div>
</div>

Don't forget to change the JDK number at the end to the one you want.

Then you will install JDK by doing this command here:

<div class="code-snippet">
  <div class="highlight">
{% highlight command %}
brew install --cask  adoptopenjdk8
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
 </div>
</div>

You may need to run `brew update` to get the latest version and access to the latest homebrew catalogue.

After it finish, you can run `which java` works on both Mac and Linux to find where the JDK installation is located.

You can type `java --version` to check the version.

![image](../assets/img/java_version.png)


Then you repeat the process and install another JDK.

You will need to find the JAVA HOME, where the JDK has been installed, for that you can run this command here:

<div class="code-snippet">
  <div class="highlight">
{% highlight command %}
find / -type d -iname "adoptopen*" 2>/dev/null
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
 </div>
</div>

Copy the path and configure your JAVA_HOME into your bash_profile, using `vi` or `vim` to edit the file using this command here:

<div class="code-snippet">
  <div class="highlight">
{% highlight command %}
vi ~/.bash_profile
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
 </div>
</div>

Add the JAVA_HOME like this:


<div class="code-snippet">
  <div class="highlight">
{% highlight command %}
#Setting PATH for JAVA
#export JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk-14.jdk/Contents/Home
#export JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home
export JAVA_HOME=/Library/Java/JavaVirtualMachines/openjdk-17.jdk/Contents/Home

export PATH=$PATH:$JAVA_HOME/bin

{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
 </div>
</div>

Finally, when you want to switch you just comment the line from the JDK you are using and uncomment the JAVA_HOME for the JDK you want to use.


After you edit the file you need to run this command here to reload it, and check the java version again.

Hope that helps, thanks until next time.


>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


