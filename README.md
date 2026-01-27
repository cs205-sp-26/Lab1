# Lab 1a — Getting Started and SSH

----------------------

## Lab goals

In this lab you will be getting started with the tools (and people) that you will work with for the rest of the semester. These include:

1. Your lab partner;
2. Getting your laptop configured;
3. Getting to know the shell;
4. Secure Shell (SSH) public / private keys;


## Due Date

Monday February 3, 2025 at 5pm

-----------------------

## Topics

Work through each of the following topics in order:

## 1. Lab Partner

Determine who your lab partner will be for the semester. We'll do this as a group. My recommendation is to avoid working with friends. Friends who work together tend to fall out; strangers who work together tend to become friends! If possible, everyone should have a partner, but it might work out where some students work on their own.

You might also consider finding a lab partner who plans to use the same OS (Mac/Windows/Linux) as you for this course.

## 2. Start setting up your local machine

Follow these instructions, depending on your OS, to start the process of configuring your local machine:

### OSX – Apple

Install Xcode from the app store.

If disk space is of concern, instead open your **Terminal** application and execute the the `xcode-select --install` command. This will provide the basic
Command Line Tool environment, providing the base programming and other development tools.

Once the Command Line Tools are installed, then you need a package manager. To install Homebrew, go to the website [https://brew.sh/](https://brew.sh/) and follow the instructions on the webpage.

### Windows

The preferred method for configuring your Windows system is to use the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/). WSL gives you access to a Linux environment without the overhead of having to manually install a Virtual Machine.

Carefully read and follow the [installation instructions](https://learn.microsoft.com/en-us/windows/wsl/install). This should install WSL on your machine and install the default Ubuntu distribution of Linux.

You can now can either launch a terminal from the start menu by searching for `WSL` or `Ubuntu`.

*Optional:* Install and get started setting up [Windows Terminal.](https://learn.microsoft.com/en-us/windows/terminal/install) This will provide you with a slightly more modern and convenient Terminal experience on Windows.

*Alternative Possibilities:* If you are unable to configure WSL, consult your lab instructor.  

### Some flavor of Linux

You are likely good to go.

## 3. Get to know the shell

A shell is a computing environment where commands can be interpreted, evaluated, and its output displayed. A good shell provides access to a rich set of commands and allows simple programming of commands, which can be used to create powerful scripts and tools. It is a common tool of professional programmers, and can be found on all three major operating systems.

### But with great power can come great frustration

Commands and their options can be terse, inconsistent, and difficult to learn. A steep learning curve often prevents novices from enjoying the eventual payoff. Whether your a shell pro or have hardly used a shell environment before, **you will want to review a more thorough tutorial.** Investing some time in learning how to use a shell will be immensely useful in this course and beyond. Spend some time with the following recommended resources or find your own preferred online tutorial:

- [Learning the Shell](http://linuxcommand.org/lc3_learning_the_shell.php)
- [software carpentry: shell-novice](http://swcarpentry.github.io/shell-novice/index.html)---this page is more of a discussion of common tasks and mistakes, advanced topics, and resources.
- You may also want to reference this online book, [the Unix Workbench](https://seankross.com/the-unix-workbench/).

### Accessing and Using Shells

- **Mac**: you can run the Terminal in Applications and pin to your Dock.

- **Windows**: You access a shell in several ways. You can right click on the Windows Icon in the Task Bar and open a terminal window. You can also type in the name of the shell program in the search bar (e.g., Cmd/Powershell/Mobaxterm).

### Deciding on a Terminal/Shell for Windows

In Windows, you can use Cmd, Powershell, or emulated shells, such as Bash for Git, Bash with Windows Linux Subsystem (WSL), Cygwin, or Mobaxterm.

`Cmd` is tried and true, and will mostly do what you want to do. The downsides are that interactions such as copy/paste are a little clunky. `Powershell` is a powerful shell, with great scripting support. However, the syntax is esoteric and inconsistent with any other shell you may use. For example, common linux commands like `cd ~ && ls` do not work in Powershell.

Enumlated shells are useful for getting a *linux-like* experience in Windows. Unfortunately, there are **many downsides to using emulated shells**. One downside is that you may be limited in accessing other executables/environments on Windows. In `Git Bash`,  environment settings you setup will not work as expected when running in Cmd/etc. Furthermore, you never truly escape Windows, for example, Windows style newline endings `'\r\n'` may exist in files you edit, which will break bash scripts. Another common problem is that when you install packages, you will often get libraries for linux binaries, which then will not work when running outside of the emulated shell. As a result, emulated shells seem helpful, but often create more problems than they solve.

My reccomendation in this course is for you to use `WSL`. You should be aware that, with `WSL`, you are actually running commands inside a small virtual machine, which limits your ability to run commands from Windows.

### Commands

99% of the reason you use shells is to run useful commands.

##### Essential commands

- **`ls`**: list content of a directory.
- **`cd`**: change directories to a new path.
- **`mkdir`**: make a new directory.
- **`pwd`**: output current directory
- **`cp`**: copy files
- **`rm`**: rm files
- **`touch`**: make a new file/update status
- **`cat`**: output the contents of a file.
- **`head`**: output the first lines of a file.
- **`tail`**: output the last lines of a file.
- **`grep`**: search files for a key phrase.
- **`wget`**: retrieve file from the web.
- **`cut`**: extract output of a file (columns)
- **`awk`** and **`sed`**: Magic commands for extracting, searching, and transforming content.
- **`nano`**: A simple command-line text editor.

## 4. Getting started with SSH

Secure Shell (SSH) is a type of terminal, allowing you to use another machine on the Internet via encrypted communication. In this course you will use your ssh credentials to access code stored on GitHub.

### Generating public/private key pairs

Being able to work with remote machines is a distinct advantage of Unix, and primarily the Internet is constructed with this type of software infrastructure. When you move between machines like this, you need to authenticate on a regular basis, which is annoying. SSH has a way around this while still preserving security. This is done by establishing a public/private key encryption that will allow the server/client components of SSH to authenticate each other.

To set up these keys do the following:

1. Open a terminal on your local machine
    - **IMPORTANT**: You should generate your keys on your local machine!
2. Run the following command (on your local machine):

```
ssh-keygen # use the default values for all prompts, i.e., just hit enter.
```

Do not enter a password. If you add a password at any point, you will need to enter a that password every time you use these credentials.

3. This will create the directory .ssh in your home directory. Change your directory with `cd ~/.ssh` and run the `ls` command to see the files that were created in that directory.
    - Note that because the .ssh directory name is prefixed with a `.` the directory is considered "hidden."
    - Use the `ls -a` command from your home directory in your terminal to show "all" files and directories, including  the hidden .ssh directory.
    - On Windows, follow [these steps](https://support.microsoft.com/en-us/windows/view-hidden-files-and-folders-in-windows-97fbc472-c603-9d90-91d0-1166d1d9f4b5#WindowsVersion=Windows_10) to show hidden folders in your file explorer.

4. In your .ssh dirctory you should now see two new files. Make note of their names. They should be something similar to, `id_rsa` and `id_rsa.pub`.
    - id_rsa is your private key. Do not share it with anyone.
    - id_rsa.pub is your **pub**lic key. You can share this with the world! Later you will upload this key to GitHub and to the CS205 server. Anyone who places this key into the authorized_keys file on their server will allow you to access your accounts on their machines password-free.

*It is very important to remember, each account will have it’s own key pairing. So if you are using different terminals in Windows, each terminal is seen as a different account and is a different pairing. The same is true if you are working on different machines, you will need to establish “a different” authentication for each machine. This is often a point of confusion for new users.*



### Important note: All steps shown from here until the section Git are for your information only. You will not perform any of these in this class 
### Installing public keys on machines you want to access

The `ssh` program allows you to run commands on a remote machine. The most basic way of doing this is to execute the following.

```
ssh 139.147.9.XXX #Where XXX are the last three digits of the ip address you want to connect to.
```

The above command will start a terminal on a different computer 139.147.9.XXX and allow you to perform any text-based command interactively.

### Different IDs

The example above did not have a specified ID, instead the ID of the account you are currently using was used as a default. This is an excellent reason to use the same ID on all of your computer accounts. But sometimes you will need to use a different account, and the following is how you would do that.

```
ssh different-id@139.147.9.XXX # if only text based programs will be used
```

### Secure Copy (`scp`)

To set up a password-less connection to a remote machine, you will need to move your public ssh key to that machine. The `scp` tool can move files between machines from the command line.

```
#scp <source> <destination>
scp some_dir_or_file USERNAME@139.147.9.XXX:/home/USERNAME/destination/
```

Here the location of the computer also includes a file system specification, which is everything after the ":". This program is useful for moving things around your systems.

### Moving your public key and setting up the server

To be able to complete the remote login process without providing any password, you will need to move a copy of the `id_rsa.pub` file. Use `scp` to copy this file from your local machine to your home directory on the potential server. Run the following command, replacing the USERNAMEs and XXX with your specific information.

```
scp ~/.ssh/id_rsa.pub USERNAME@139.147.9.XXX:/home/USERNAME
```

Once you've copied your public key to the server, you'll need to `ssh` to the server one last time using your password.

Run the following command **on the server** to append the contents of your public key into the authorized_keys file:

```
mkdir .ssh
cat id_rsa.pub >> .ssh/authorized_keys
```

Now you should be able to `ssh` to the server without being prompted for a password.

### Important points of public key installation

This is a list of things to keep in mind as you continue to work with public/private keys.

- Create a public and a private-key on a machine that will be logging into another computer.
- Always leave the private-key untouched. If you accidentally generate a new private-key, then all distributed public-keys
are now invalid.
- The public-key, stored in id_rsa.pub can be shared with anyone that will let you have access to their machine. So copy
that key to other machines.
- Access the other machine using ssh and your lab account id, then install the key you copied there into the authorized_keys
file.
- Test that your key is working by exiting out of the machines where you installed the key and then logging back it. You
should not be asked for a password.
- You should do this for all machines that you plan use for this course, and in the future.
