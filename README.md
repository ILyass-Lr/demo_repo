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

To put it in GitHub we run the: `git push origin main` command. 

- origin: specifies the location of the repository
- main: is the branch we push into.

⚠ *Note:* Before making changes to your code, always make sure that you are making changes to the last version, you could pull the last changes from GitHub by the command: `git pull origin main` which combine two commands:
- `git fetch origin` : This will download the changes from the remote repository but will not merge them into your local branch yet.
- `git merge origin/main`: After fetching, merge the changes into your local main branch.

## Git  Branching
Branching is useful when you want to add some features or fix a bugs that your fear is going to break your code, and thus creating a branch separated from the master branch is the way to go, the commits made on a branch doesn’t affect other branches, When you’re sure about the code, you can merge with the master branch or any branch you like.
To list available branches, run: `git branch`

```bash
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git branch
* main
```

To create a new branch do: `git checkout -b feature-readme-instructions` with the name of the branch being *feature-readme-instructions*

```bash
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git checkout -b feature-readme-instructions
Switched to a new branch 'feature-readme-instructions'
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git branch
* feature-readme-instructions
  main
```

To switch between branches, you can use `git checkout branchName`

```bash
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git branch
  feature-readme-instructions
* main
```

If you want to see the difference between two branches, you can go back to the main branch and run: `git diff feature-readme-instructions`

If you change back to the main branch you won’t find the changes made in the feature-readme-instructions because the branches are separated. Now to merge the changes you have two option:

- Switch to the main branch, and the run: `git merge feature-readme-instructions`.
- Switch to the feature-readme-instructions branch, push the changes to GitHub: `git push -u origin feature-readme-instructions`, and then make a pull request.
    
For the second option On GitHub: Click on Compare & pull request



You can check all the comment related to your PR, the commits on that branch, and the changes compared to the main branch



You can now merge the branch if you are the owner of the main branch



But if you changed to the main branch locally, you won’t find the changes there because they are on GitHub. You need to run git pull (without the origin main if the upstream was already set)

In many Case when you merge branches, you won’t be using the one you just merged and this you can delete it by: git branch -d branchName
```
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git branch -d feature-readme-instructions
Deleted branch feature-readme-instructions (was 6bc10d0).
```
### Merge Conflicts
When there there are many branches being merged to a master branch, Git sometimes doesn’t know which code to keep and which to discard, and create a merge conflict, we are going to simulate this, and see how to deal with it.

Firstly, we create a new branch called *quick-test* by `git checkout -b quick-branch`, we modify the index.html file and we track and commit the changes at the same time by the command: `git commit -am “Added Hello World”`
```html
<div>Git !! You need to track me too !</div>
<p>Hello World !</p>
```
Note that this command works only for modified files !
```
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git commit -am "Added Hello World!"
[quick-test 035e060] Added Hello World!
 1 file changed, 2 insertions(+), 1 deletion(-)
 ```
We’re going back to the main branch to add a second line there also that will provoque the merge conflict, the we will add and commit the changes to the main branch.
```html
<div>Git !! You need to track me too !</div>
<p>A merge conflict is created because of me :D</p>
```
When we try to merge now, we get a merge conflict
```
PS C:\Users\lenovo\Desktop\Projects\Learn_git\demo_repo> git merge main
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```
You can handle the conflicts on the termina or in VS Code by either deleting one of the lines, or adding both of them



