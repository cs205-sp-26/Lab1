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

# Lab 1b: Git

## Lab goals

In this part of the lab you will be working with Git, which is a fast, scalable, distributed version control system with a rich command set that provides both high-level operations and full access to internals. It lets you share a developing resource to which one or more people can contribute over time. Through specific commands, it stores things as a sequence of changes, allowing you the ability to comment on changes that are being made. If two developers are contributing to the same piece of code, then commit (submit) these pieces of code, Git will facilitate combining (merging) the code.

The general structure of a git repository is that there are multiple repositories, where one git repository starts as the origin and additional repositories are "cloned." Clones are called working repositories and belong to the developer working in/on their personal, local environment/machine. This allows each developer to do their own work without being connected to the originating repository, but then occasionally sync up the work being done.

For this lab, you and your partner will clone a git repository from GitHub to your account on your local machine and on the lab machine. Then you will explore Git a bit to help set up for the coming semester. Note — I will be adding myself to your lab account and checking out a copy of your running labs. 

## 0. Create or sign in to your GitHub Account
GitHub is a platform for storing and sharing code using Git. It allows multiple people to collaborate on a project, manage different versions of code, and easily revert to previous versions if needed. Developers use GitHub to host projects, contribute to open-source software, and work together on coding tasks efficiently.

Navigate to [github.com](github.com) and create an account (if you don't have one already).

Once you have signed into your account, use the link posted on Moodle to get access to your lab1b repository.

## 1. Add your public key to your GitHub account
First, you will need to add your ssh key (id_rsa.pub) to your GitHub account. GitHub provides a handy set of instructions for completing this step. Follow along [here](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account). Make sure you are adding your key to the GitHub account you are using for this class and not another personal account. If you are using Mac, be sure to follow the Mac instructions. If you are using WSL, you will follow the **Linux** instructions.

### Testing your configuration
Now let's test to see if GitHub recognizes your ssh key. Run the following command from your local terminal:

```
ssh -T git@github.com
```

You should see:

```
> Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

### Debugging failed connections
Should you receive an error message when trying to test your ssh connection to GitHub, try these troubleshooting steps.

#### Mac
Run the following command to see if your key has been added to the ssh agent

```
ssh-add -l
```
You should get a response with the key fingerprint of the private key you want to use. If instead you get the message The agent has no identities or Could not open a connection to your authentication agent, then you will need to add your private key:

```
ssh-add ~/.ssh/id_rsa
```

This problem may reemerge when you restart your machine and/or terminal. If it does, simply rerun the ```ssh-add ~/.ssh/id_rsa``` command.



## 4. Summary of your configuration so far
Having completed the steps so far, you can now push and pull code from your local machine to GitHub via ssh. Congratulations! 


The following diagram depicts what you have configured so far:
```
---------------------      ssh      ---------------------
| Your Local Machine|   <--------> |       GitHub       |
---------------------               ---------------------
```

You are now ready to practice working with some basic git commands.

## 5. Git'ing started

Git is one of the most widely-used version control tools in industry. As you will see in the remainder of this lab assignment, it's easy to get started! However, there are many useful git features that this lab will not cover. I'd strongly encourage you to spend some time familiarizing yourself with git, since you'll be using it for the rest of the semester (and perhaps long into the future). There are quite a few well-done online tutorials:

- [git-it](https://github.com/jlord/git-it-electron/releases)
- [git branching](https://learngitbranching.js.org/)
- [visualizing git](http://git-school.github.io/visualizing-git/)
- And many more...

## 6. Cloning your first repository
For this exercise, you will clone an existing repository onto your local machine from GitHub and make a few changes to the code I have provided you with.

First, let's make a directory to hold this repository. On your local machine run:

```
cd ~          # Make sure we are in our home dir
mkdir labs    # Make a new dir for the repo
cd labs       # Move to the new dir
```

Now follow [these instructions](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository#cloning-a-repository) to clone your team's lab-1b repository. **Make sure to select "ssh" option instead of "https" when copying the link.**

The instructions linked above conclude with you running the following command on your local machine:
```
git clone git@github.com:YOUR_USER_NAME_HERE/lab-1b.git
```

To confirm that everything was cloned correctly:
```
cd lab-1b
ls          
>README.md  test.sh #You should now see these three files
```

You can also test running the shell script:
```
./test.sh
```

The next step is to make your Git repository aware of who you are, to be able to identify you in the changes you will be making. Both lab partners should execute the following commands with their respective information.

```
$ git config --global user.name "Justin Smith"            # Obviously, replace with your name
$ git config --global user.email smithjus@lafayette.edu   # and your email
$ git config --global pull.rebase false                   # tell git how to handle pulls
```

(Optional) Next choose a default editor. You can change this later, but this will set you to use the simple Nano editor common to most systems instead of vi or vim.
`$ git config --global core.editor nano`

## 7. Making changes

The next steps will get you started with the main Git commands. Note that from here forward, I will prefix commands with a '$' to differentiate them from output.

First thing that needs to be done is to create some content. One lab partner should execute the following commands on their machine:

```
$ mkdir test
$ git add test
$ cd test/
$ touch file
$ cd ..
$ git add test
$ git commit -m "Added test dir"
  [master (root-commit) 3a4a2f3] Added test dir
  1 file changed, 0 insertions(+), 0 deletions(-)
  create mode 100644 test/file
$ git push
  Counting objects: 4, done.
  Writing objects: 100% (4/4), 247 bytes | 0 bytes/s, done.
  Total 4 (delta 0), reused 0 (delta 0)
 ...
 * [new branch] master -> master
```

The various outputs should appear as you execute the commands. The one new command here is touch, which creates a new file. The three commands following the git command are:
  - add – adds the entire directory to the Git staging area;
  - commit – finalizes the changes to the local repository;
  - push – moves/pushes the repository to the origin repository.

If you forget to include a message (using the -m option) with the commit command, you may find yourself in the vi editor. If you do find yourself here, type in your message and then type the following key combination ":wq". The colon places the editor into command mode, the "w" means write, and the "q" indicates quit.

Once these commands are complete, the other lab partner can execute git pull to retrieve the information stored in the origin repository.

```
$ cd lab_1b/
$ git pull
```

This should result in producing a duplicate directory in the lab partner's directory. Examine the directory to be sure this has happened. The next step is for the lab partner who pulled the information from the origin repository. They should open the file "test/file" with the nano program (or their preferred text editor), modify it, and save the file. 

```
nano file
```

Once they have done this, they should run the following command:

```
$ git status
 On branch master
 Your branch is up-to-date with 'origin/master'.
 Changes not staged for commit:
 (use "git add ..." to update what will be committed)
 (use "git checkout -- ..." to discard changes in working directory)
 modified: test/file
 Untracked files:
 (use "git add ..." to include in what will be committed)
 test/file~
 no changes added to commit (use "git add" and/or "git commit -a")
```

The information displayed is Git's way of helping you figure out what to do. Thus you should follow these steps:

```
$ git add test/file
$ git status
 On branch master
 Your branch is up-to-date with 'origin/master'.
 Changes to be committed:
 (use "git reset HEAD ..." to unstage)
 modified: test/file
 Untracked files:
 (use "git add ..." to include in what will be committed)
 test/file~
$ git commit -m "Updated the files"
 [master d6979f7] Updated the files
 1 file changed, 1 insertion(+)
$ git push
 Counting objects: 4, done.
 Writing objects: 100% (4/4), 303 bytes | 0 bytes/s, done.
 Total 4 (delta 0), reused 0 (delta 0)
 To ssh://139.147.9.134/home/lab_1_11/repo_member1_member2.git
 3a4a2f3..d6979f7 master -> master
```

Complete this step by having the other (first) lab partner execute a git pull.

To find out what is going on, one can always use the `git log` command. Both lab partners should execute this command.

These basic steps are the essentials of working with Git. But there is one situation that can be tricky, which arises when both lab partners modify the same file(s) simultaneously. To simulate this, both partners should add their name to the first line in the file, both then execute an add and a commit. Then one of the lab partners should do a push, while the other partner waits.

```
$ git push
 Counting objects: 4, done.
 Writing objects: 100% (4/4), 316 bytes | 0 bytes/s, done.
 Total 4 (delta 0), reused 0 (delta 0)
 ...
 d6979f7..db34a9d master -> master
```

Now the other partner should attempt a push.

```
$ git push
 To ...
 ! [rejected] master -> master (fetch first)
 error: failed to push some refs to
 ...
 hint: Updates were rejected because the remote contains work that you do
 hint: not have locally. This is usually caused by another repository pushing
 hint: to the same ref. You may want to first integrate the remote changes
 hint: (e.g., 'git pull ...') before pushing again.
 hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

Things seem broken – time to correct them by first pulling the first lab partner's code.

```
$ git pull --rebase
 remote: Counting objects: 4, done.
 remote: Total 4 (delta 0), reused 0 (delta 0)
 Unpacking objects: 100% (4/4), done.
 ...
 d6979f7..db34a9d master -> origin/master
 Auto-merging test/file
 CONFLICT (content): Merge conflict in test/file
 Automatic merge failed; fix conflicts and then commit the result.
```

The reason for the conflict will become obvious. To correct it, look in the file and see where the issue is identified.

```
$ cat test/file
 two I have added something...
 one I have added something...
```

The correction should come in the form of modifying the file to resolve the differences and removing the three lines that were added by Git. You can see the resolution I took below.

```
$ nano test/file
$ cat test/file
 I'm keeping both. We are a team!!!
 two I have added something...
 one I have added something...
```
Now use git add, commit and push the file.

```
$ git add test/file
$ git commit -m "cleaning up conflict"
 [master d2af95a] cleaning up conflict
$ git push
 Counting objects: 8, done.
 Delta compression using up to 8 threads.
 Compressing objects: 100% (3/3), done.
 Writing objects: 100% (8/8), 647 bytes | 0 bytes/s, done.
 Total 8 (delta 0), reused 0 (delta 0)
 To ...
 db34a9d..d2af95a master -> master
```

The other lab partner should now see the negotiated change by executing a git pull.
Experiment further with the basic operations until you feel comfortable with what is going on. You can find further information via the "git help" command.



## Submission
Submission will be by the instructor examining your repository and your lab account. This assignment will be graded based on your organizational skills, and I will be examining your server accounts. Please remove any un-needed SSH entries from your authorized_hosts file, be sure to remove any un-needed files, and properly identify the files that remain. I will be checking to see that both lab partners contributed to and resolved merge conflicts in your shared git repository.
