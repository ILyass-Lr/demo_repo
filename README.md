# Introduction to Git & GitHub

## Creating Files and Commiting changes on GitHub (_Online_)

You do that by clicking **Add file > Create new file**, enter its name and then clicking the green _Commit changes_ button at the top-right corner

![image](https://github.com/user-attachments/assets/2840d631-0b11-4fbf-81b2-eb2610754507)

For this Demo we are creating and committing a `README.md` file

**Note:** GitHub can render markdown files, and by default render the `.md` file found in your repository, generally bieng the READNE.md file.

After Clicking on _Commit changes_, you'll be prompted to enter a Commit message describing the new changes related to this commit.

![image](https://github.com/user-attachments/assets/c7440793-be0f-4ad7-a5d4-7e7f4d349cda)

To access all your Commits, click on the Commits button

![image](https://github.com/user-attachments/assets/325c94d8-a5ef-423c-802c-039640e2ed01)

You'll see a list of all commits with their unique code, when choosing one, you'll see all the changes made, The red is for the line that are removed, the green is for the lines that are added, and the no-colour ones for the lines that haven't changed.

![image](https://github.com/user-attachments/assets/6cad5082-8d86-48b8-a7e0-54f31a80c848)


## Using git in local machine

For that You’ll need to install Git for your current OS, then open the folder where you want to have the project on in an IDE, (VS Code in our case), then the terminal

![image](https://github.com/user-attachments/assets/aaba3edb-3d62-4812-9855-2645387b7ca4)

There are many ways to clone your repo, but we will proceed by an SSH Key, for that we need to create a new SSH Key by going to the SSH and GPG Keys Settings and then clicking New SSH Key

### SSH Keys

To be able to push your local code to GitHub you need an SSH Key that can be made by the `ssh-keygen -t rsa -b 4096 -C “email@gmail.com”`

- `-t` : the type of encryption algorithm, can be:
    - `rsa`
    - `ed25519` which is a  modern algorithm that is faster and more secure than RSA for most purposes. It does not use the `-b` flag because the key size is fixed.
    - **`dsa`**: Digital Signature Algorithm, now considered outdated and less secure.
    - **`ecdsa`**: Elliptic Curve Digital Signature Algorithm, another modern alternative
- `-b` : the number of bits the key contain, the more there are, the harder it is to break.
- `-C` : the associated email

The command generate two keys:

- A private key without extension: used when ever you want to connect to GitHub or push your code in GitHub or use your account via your local machine. It is the one that generated the public Key.
- A public Key with the *.pub* extension: that is put in GitHub.

Run the SSH Agent:
```
$ eval "$(ssh-agent -s)"
Agent pid 345
```
Add the following line in the config file in the .shh folder (create a config file if not present)
```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/ssh-key
```
Add the SSH-Key to the SSH-Agent:
```
$ ssh-add ~/.ssh/ssh-key
Identity added: /c/Users/lenovo/.ssh/ssh-key (email@gmail.com)
```
### Making changes (*locally*)

Navigate to the repo folder by : `cd demo-repo`, add changes to existing file or make new files, or delete existing files, and when finished, you can track the new changes by the `git status` command:
```
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git status
● On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html

no changes added to commit (use "git add" and/or "git commit -a")
``` 

We have a modified file and a new file that is untracked with Git, to track it we can either do `git add .` to track all files changes in the current folder or `git add index.html` for the specific _index.html_ file. When running `git status` again, you'll see all your files tracked and ready to be committed

```
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   index.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
```

We commit our changes by the `git commit -m "Why you committed" - m "More details".` Till now we have committed the changes in our local machine.

To put in GitHub we run the: `git push origin main` command. 

- origin: specifies the location of the repository
- main: is the branch we push into.




