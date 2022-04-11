# **Week 2 Lab Report**

In this week's report we will be showing you how to set up your course specific account with a remote access. Many classes use course-specific accounts so it is important for us to set up our personal machines to connect to a remote computer over the Internet to do work over there.

## Step 1: Installing VScode
-----------------------
There are many different platforms to code and set up remote access, but we will be focusing on doing most of our work through **Visual Studio Code**. 

1. Go to the [VScode](https://code.visualstudio.com/) website and click on the blue "Download" button on the top right. Depending on the which platform you are working on, either click on the Windows, Linux, or Mac download button and follow the steps after to complete downloading.
![vsc_dl_img](https://i.gyazo.com/96854060b685094b15a128b501d88065.png)
2. Once you follow the downloading steps you should have a vscode open 
![vsc_img](https://i.gyazo.com/f773976eb1c082363ab47e258a29cd25.png)

## Step 2: Remotely Connecting
----------
We will continue to vscode throughout the entire remotely-connecting process, but we first have to install a program called **OpenSSH** which will be our connecting device in vscode. *This will be the most important step in this writeup and for future usage so it is crucial to follow these steps carefully.*

*We will be using Windows as our main guiding tool.*
1. To download OpenSSH we first want to type in our home search bar and type in "Optional Features". It should look something like this ![openssh_img](https://i.gyazo.com/c3cce5d8a5fddb057b09909bcf0fded1.png)
From here click on "View features", then:
    * Search **OpenSSH Client** and install.
    * Search **OpenSSH Server** and install.

    After you complete those steps, find your course-specific account info by logging into [here](https://sdacs.ucsd.edu/~icc/index.php). *You might be asked to change your global password or other passwords change.*

    Once you log in you will find under "Additional Accounts" your course-specific account.(For this class it will be your cs15l account). You will be using this code to log in to your remote access. ![cs_acc_img](https://i.gyazo.com/2e3a6628589f2a078c68b82ae54237b6.png)

2. After installing OpenSSH and receiving your course-specific account info, we then want to go back to VScode to connect the two together. 

*(All the steps below are instructed in [this website](https://code.visualstudio.com/docs/remote/ssh#_connect-to-a-remote-host)*

* Open vscode and on the top left selection bar, we want to run the Terminal and type in the command:

    `$ ssh cs15lsp22zz@ieng6.ucsd.edu`
    
    Because this will most likely be your first time logging in you will have this interaction 
    ```
    ⤇ $ ssh cs15lsp22zz@ieng6.ucsd.edu

    The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.

    RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.

    Are you sure you want to continue connecting (yes/no/[fingerprint])?
    ```
    Make sure you type in 'yes' after. There is a deep description on this piece of text but we won't go into detail on that. After typing in 'yes' your next set of interactions will look like:
    ![remote_access_img](https://i.gyazo.com/eb9775a68c888e5681afdf6d3d9d8e35.png)

    We have now connected to through remote access! Instead of working under our personal computer's data space, we now will run our following commands to a computer in the CSE basement. 

## Step 3: Trying some commands

Now that we have opened a remote-access account let's try and run a few commands. Try running the commands `cd, ls, pwd, mkdir, and cp` in different ways. Compare how the different commands function when running on *your* computer, and on the remote computer. Try and see what causes error. Explore your limits! 

>Some other useful commands you can try are:
- cd ~
- cd
- ls -lat
- ls -a
- ls < directory >
- cp /home/linux/ieng6/cs15lsp22/public/hello.txt ~/
- cat /home/linux/ieng6/cs15lsp22/public/hello.txt

![ra_cmd_img](https://i.gyazo.com/1f87c70117d5302681b059651e40b4c9.png)

## Step 4: Moving Files with scp
One of the main reasons why we work with a remote computer is the ability to move files between your main computer and the remote one. We will be using the `scp` command to move files, and we can only use this cmd on your personal computer.(Not the computer logged into your ieng6). 

- Create a file called `WhereAmI.java` and copy the following code:

```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
Try and running it using:

`javac WhereAmI.java`

`java WhereAmI`

After examining the output, run the following scp command to copy the file onto your remote computer: 

`scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu:~/`

Follow the following steps in your terminal like this: 
![scp_cmd_img](https://i.gyazo.com/40e22c3b56f85716827c3a0d2349f8d1.png)

## Step 5: Setting an SSH Key
Looking at the previous step, we notice that everytime we want to use scp and ssh to copy files we have to type in our password each time. This is very inconvenient for coders, so in order to work around that we create what is called **"SSH Keys"**. 

First copy the following interaction below on terminal: 

-------

![sshkey1_img](https://i.gyazo.com/9e804092ffbe8ecc68e1f0dcbda75aba.png)

![sshkey2_img](https://i.gyazo.com/843d5e11d5badf469f51a420a9caa41e.png)

These two interactions will create two new files: a private key and a public key that is stored in the ssh directory. 

After this follow run the following commands in terminal:
```
$ ssh cs15lsp22zz@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22zz@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above
```
This will complete the ssh-key process. If you attempt to log back into your ssh acc you will no longer require a password like this:

![sshkey_final_img](https://i.gyazo.com/5056af74052d11729d8179ec6c325143.png)


## Step 6: Optimizing Remote Running
We have learned lots of new info in these past 5 steps, and with that information we can combine them all together to make the whole process a little more pleasant. 

One of the most simple ways to optimize remote access is to run a command in quotes right after an ssh login.
![optim_img](https://i.gyazo.com/fadf3163a4fc1d6e8f90204f7584e2fd.png)
As you can see we put two commands in one single line and it saved up valuable time as coders.
