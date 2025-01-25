# Introduction to Git & GitHub
## Creating Files and Commiting changes on GitHub (_Online_)

You do that by clicking **Add file > Create new file**, enter its name and then clicking the green _Commit changes_ button at the top-right corner

![image](https://github.com/user-attachments/assets/2840d631-0b11-4fbf-81b2-eb2610754507)

For this Demo we are creating and committing a README.md file

**Note:** GitHub can render md files, and by default render the .md file found in your repository, generally bieng the READNE.md file.

After Clicking on _Commit changes_, you'll be prompted to enter a Commit message describing the new changes related to this commit.

![image](https://github.com/user-attachments/assets/c7440793-be0f-4ad7-a5d4-7e7f4d349cda)

To access all your Commits, click on the Commits button

![image](https://github.com/user-attachments/assets/325c94d8-a5ef-423c-802c-039640e2ed01)

You'll see a list of all commits with their unique code, when choosing one, you'll see all the changes made, The red is for the line that are removed, the green is for the lines that are added, and the white for the lines that haven't changed.

![image](https://github.com/user-attachments/assets/6cad5082-8d86-48b8-a7e0-54f31a80c848)


## Using git in local machine

For that You’ll need to install Git for your current OS, for that we need to create a new SSH Key by going to the SSH and GPG Keys Settings and then clicking New SSH Key


You enter a descriptive title for your SSH Key, the Key Type (Authentification for this case), and the key.

To generate the Key, open Git Bash that is Installed after installing Git

```
$ ssh-keygen -t ed25519 -C "lirmaqui.ilyass@gmail.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/lenovo/.ssh/id_ed25519): /c/Users/lenovo/.ssh/ilyass_ed25519
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/lenovo/.ssh/ilyass_ed25519
Your public key has been saved in /c/Users/lenovo/.ssh/ilyass_ed25519.pub
$$ eval "$(ssh-agent -s)"
Agent pid 345
$ ssh-add ~/.ssh/ilyass_ed25519
Identity added: /c/Users/lenovo/.ssh/ilyass_ed25519 (lirmaqui.ilyass@gmail.com)
$ cat ~/.ssh/ilyass_ed25519.pub
```

Follow the prompts to save the key to the default location, and add your SSH key to the ssh-agent, lastly copy the key and paste it in the Key field at GitHub

Now back to yourfo folder:

```
PS C:\Users\lenovo\Desktop\Projects\Learn_git> git clone git@github.com:ILyass-Lr/demo_repo.git
Cloning into 'demo_repo'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
```

Navigate to the repofo folderby : `cd demo-repo`,addc hanges to existing file or make new files, or delete existing files, and when finished, you can track the newc changes by the `git status` comand:
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

We have a modified file and a new filet that is untracked with Git, to track it we can either do `git add .` to track all files int the current folder or `git add index.html` for the specific _index.html_ file. When running `git status` again, you'll see all your files tracked and ready to be committed

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

We commit our changes by the `git commit -m "Why you committed" - m "More details"`







