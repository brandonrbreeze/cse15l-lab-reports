**Step 1: Intstall VS Code**
![Image0](/VS-code.png)

To download VS Code go to https://code.visualstudio.com/.

Choose the appropraite version for your operating system.
As you can see I already had VS code downloaded for my Mac.

**Step 2: Remotely Connecting**
![Image1](/remotely-connecting.png)

To connect to a remote server open a terminal in VS Code and type: 
ssh cs15lfa22zz@ieng6.ucsd.edu.  
You will be prompted to enter a passcode.  After you enter you passcode properly you should be connected to the server.  If it's the first time connecting to the server you may be asked if you would like to continue connecting.  Type yes to continue.

**Step 3: Running Some Commands**
![Image2](/someCommands.png)

In this step I ran some commands. The first command that I ran was ls. ls lists the contents of the current directory.  The next command I ran was ls -a. This command lists all the contents of the current directory including hidden files.  Finally, I ran the cat command. This command output the content of a file to the terminal.

**Step 4: Moving Files with scp**
![Image3](/scp1.png)

In this step we moved a file from the client to the server using the command: 
scp WhereAmI.java cs15lfa22rg@ieng6.ucsd:~/
This command makes a secure copy of WhereAmI.java and sends it to the home directory of the remote server cs15lfa22rg@ieng6.ucsd

![Image4](/scp2.png)

To check that the file was copied, I used ssh to remotely to the server.  Then I used ls to check to see if the file was there.

**Step 5: Setting an SSH Key**
![Image5](/keygen.png)

The first step in setting an ssh key was to generate one on the client using ssh-keygen which generated a unique key that we are going to copy into a specified location on the server which will allow ssh to use the keys as a password

![Image6](/mkdir.png)

Then next step was to make a loction on the server to put the public copy of the ssh key. As you can see i already had a ssh directory. I wanted to show how make a directory usign the mkdir command. So I removed the directory using rmdir then remade it.

![Image7](/scp-sshkey.png)

After the location is set, we are able to make secure copy using scp:
scp /Users/brandonbreeze/.ssh/id_rsa.pub cs15lfa22rg@ieng6.ucsd.edu:~/.ssh/authorized_keys

Interestingly, we didn't have to make authorized keys. It was automaticly configured.
After the file is copied, we are now able to use ssh and scp commands with this server without having to give a password

**Step 6: Optimizing Remote Running**
![Image8](/Optimized.png)

I started by writing two commands:
scp WhereAmI.java cs15lfa22rg@ieng6.ucsd.edu:~/
ssh cs15lfa22rg@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"

To go from saving on the client to running on the server all you have to do is save the file, then click on the terminal, press up twice to get the scp command, then press up twice to ssh in and run