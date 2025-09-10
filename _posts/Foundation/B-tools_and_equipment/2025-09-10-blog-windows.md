---
toc: False
layout: post
data: tools
title: Setting up Windows Tools from scratch!
description: Setup guide for using Windows Subsystem for Linux (WSL) for development.
categories: ['DevOps']
author: Anish Gupta
permalink: /blogs/windows-setup-blog
breadcrumb: True 
---
 
# Setting up Tools on Windows
 
Windows OS is one of the most widely used operating systems, but it lacks support for many common tools which are native to Linux and other UNIX type systems (e.g. MacOS). In 2016, Microsoft released the **Windows Subsystem for Linux (WSL)** that allows you to interact with a Linux terminal on your Windows laptop or PC!
 
![Graphic of WSL](https://linuxkamarada.com/files/2025/03/wsl-en.png)
 
## 1. Install/Setup Visual Studio Code
 
VSCode is an integrated development environment (IDE) that we can write code in.
 
1. Download Visual Studio Code from [this website](https://code.visualstudio.com/)
 
2. Ensure that VSCode is added to your PATH
	- During installation, check the box “Add to PATH” in the setup wizard.
 
	- This enables you to open VSCode directly from a terminal using `code .`
 
	- If you missed this step, you can fix it by doing the below steps:  
		- Open the Start menu, search for Environment Variables, and click Edit the system environment variables.
		- In the System Properties window, click Environment Variables….
		- Under System variables, find and edit the Path variable.
		- Add the path to your VSCode installation (e.g., `C:\Users\<YourUser>\AppData\Local\Programs\Microsoft VS Code\bin` ).
 
## 2. Install Git
1. Install the Git Config Manager from [this website](https://git-scm.com/downloads/win). Make sure to download the correct standalone installers.
 
2. Click the default option on each prompt.
 
 
## 3. Install WSL (Ubuntu 22.04)
1.  **Open Windows Terminal**
    -   Search for Windows Terminal in the Start menu.
 
-   **Install Ubuntu 24.04 under WSL**
 
    -   Run: `wsl --install -d Ubuntu-24.04`
 
    -   When prompted, create a **username** and **password** for your Linux account. While entering the password, you won’t see characters echoing- don't worry, this is normal.
 
-   **Exit the Ubuntu shell after setup**
 
    -   When the install finishes you’ll be at an Ubuntu prompt, so type `exit` to leave the WSL session.
 
-   **Make Ubuntu 24.04 the default WSL distribution**
 
    -   Run: `wsl --set-default Ubuntu-24.04`
 
-   **Launch WSL anytime from Windows**
 
    -   From the Windows terminal, type `wsl` to start your default Linux distribution.
 
## 4. Clone Repo
 
_Note: UNLESS STATED OTHERWISE: Assume all commands listed from this point onwards are in WSL: and NOT on your Windows Terminal._
 
1. Create a new folder for your repositories with the `mkdir` command.
	- You can organize your folders however you want. I have one folder called `neur0n-7` for my student repo, one called `opencs` for the pages repo creating by Open Coding Society, and one called `CompSciTeam` for my team repo.
 
2. In your folder, run `git clone https://github.com/[YOUR USERNAME]/student.git`.
	- For example, I would run `git clone https://github.com/neur0n-7/student.git`.
 
## 5. Run Setup Scripts
 
1. **ON YOUR WINDOWS TERMINAL**, `git config --global credential.helper "/mnt/c/Program Files/Git/mingw64/bin/git-credential-manager.exe"`
2. Run the activation script to set up git and packages: `./scripts/activate.sh`
3. Run the setup script for your virtual environment: `./scripts/venv.sh`
4. Run `source venv/bin/activate` before making code!
 
## Optional step: system checks
 
Just to make sure everything works fine :)
 
```
python --version
pip --version
ruby -v
bundle -v
gem --version
git config --global --list
```
 
If any of these fail, go back and retry the steps from above (especially step 5!).