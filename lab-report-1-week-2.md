

# CSE 15L Week 1 Lab: Logging into ieng6 course-specific accounts
[Home](index.html)
1. Install VSCode
2. Connect to the remote server
3. Commands
4. Move files using scp
5. Set up SSH key to log in faster
6. Optimizing remote running

## Install VScode
The first step is to download VSCode. I already had it downloaded, but if you don't have it, you can download it here: [VScode download](https://code.visualstudio.com/).

![Image](report1_vscode.png)

## Connect to remote server
Next, to connect to the remote server, make sure you have SSH downloaded (if on Windows) and that you have the name of your course account. Then open a terminal in VScode using Terminal -> New Terminal. The command to connect to the remote server is:

```
ssh cs15lwi22zaao@ieng6.ucsd.edu
```
Enter your password, and you should be able to connect.
![Image](report1_sshcommand.png)

## Try out commands
Here are some useful commands to try both in your local environment and on the server.
- `cd` - change directory
- `ls` - list files (-a shows hidden files). `dir` is similar for Windows
- `pwd` - print working directory
- `mkdir` [name] - make directory
- `cat` [file name] - prints contents of file
- `exit`, `logout`, or ctrl-d - log out of the remote server

![Image](report1_commands.png)