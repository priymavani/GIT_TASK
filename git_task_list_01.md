

## Part 1: Introduction to Version Control and Git

### **Task 1: Install and Configure Git**
1. Configure Git with your username and email 
    ```bash
    git config --globle user.name "priymavani"
    git config --globle user.email "priymavani@gmail.com"  
    ``` 
    ↦ Golbal = Settings that apply to all repositories for the current user.

    ↦ Local = Settings that apply only to a specific repository.
    ↦ System = Settings that apply to all users on the system.
    
    ↦ to link github account to local (globally) by user name and email


 2. View your Git configuration:
    ```bash
    git config --list
    ```

    ↦ to show detail of configuration variable(user.name , user.email) and value
   
#### **Task 2: Initialize a Repository**
1. Create a new project folder and navigate to it:  
     ```bash
      mkdir MyProject
      cd MyProject
     ```
     ↦ mkdir to make folder and cd to navigate into folder
2. Initialize it as a Git repository:  
   ```bash
   git init
   ```
   ↦to initilize folder (make folder ready to connect with repo)

   Example:  
   After running `git init`, a hidden `.git` folder will appear in the directory, indicating it’s now under version control.

#### **Task 3: Create a File and Make Multiple Commits**
1. Create a new file and add content:
   ```bash
   echo "My First Project" > README.md
   ```
   ↦to make file or change file content by "content to write or edit"

2. Stage the file:  
   ```bash
   git add README.md
   ```
   ↦ to add file to staging area ( stores information about what will go into your next commit)

3. Commit the file:  
   ```bash
   git commit -m "Initial commit: Added README.md"
   ```
   ↦ commite the added file to save change (save point)

4. Make changes to the file:  
   ```bash
   echo "Added a description" >> README.md
   ```
   ↦ edit the file content

5. Stage and commit the changes:  
   ```bash
   git add README.md
   git commit -m "Updated README with a description"
   ```
   ↦ to add and save the content by commit

#### **Task 4: Check Status and Log**
1. Check the repository’s current status:  
   ```bash
   git status
   ```
   ↦ to know the file is in staging area and know on which branch we are


2. View commit history in detail:  
   ```bash
   git log --oneline --graph --decorate
   ```
   ↦ to know branch , commit history in one line

   Example Output:  
   ```
   * 2f8d6a2 (HEAD -> main) Updated README with a description
   * d3c4b21 Initial commit: Added README.md
   ```

#### **Task 5: Create and Clone a Repository**
1. Create A repository on GitHub named ` example-repo`.
2. Clone it locally :
   ```bash
     git clone http:codinggita.com/example-repo
   ```
   ↦ to clone github repo into local folder

#### **Task 6: Understanding the Git Workflow**
- Example Workflow:
 
  i. Make Changes to a file in the working directory:
   ```bash
    echo "Workflow example" >> workflow.md
   ```
   ↦ make a new file
  ii. Stage the file:
   ```bash
     git add workflow.md
   ```
   ↦ added to staging area
  iii.Commit the file to the repository:
   ```bash
    git commit -m "Added workflow example"
   ```
   ↦ save the chage of staging area

---

### **Part 2: Working with Repositories**

#### **Task 7: Branching and Merging**
1. Create a new branch for a feature:  
   ```bash
   git branch feature-login
   git checkout feature-login
   ```
   ↦ makinging new branch feature-login
   ↦ shifting to branch feature-login

   Or use:  
   ```bash
   git checkout -b feature-login
   ```
   ↦ checkout -b to create new branch and swift to new branch (two process in one command )

2. Add a new file and commit changes:  
   ```bash
   echo "Login Page" > login.html
   git add login.html
   git commit -m "Added login page"
   ```
   ↦ creating new file
   ↦ adding to staging area
   ↦ commit the change 

3. Merge the feature branch into `main`:  
   ```bash
   git checkout main
   git merge feature-login
   ```
   ↦ all the change in branch feature-login will combine to mai branch 

#### **Task 8: Handling Merge Conflicts**
1. Create two branches:  
   ```bash
   git branch branch-A
   git branch branch-B
   ```
   ↦ to create branch-A and branch-B
2. Modify the same line in `README.md` in both branches. 
   ↦ switch to branch-A ,edit the file , add to staging area and commit the change 
   ↦ switch to branch-B ,edit the file , add to staging area and commit the change 
3. Merge `branch-A` into `main`:  
   ```bash
   git checkout main
   git merge branch-A
   ```
   ↦ switch to branch main, merge branch-A with main
4. Attempt to merge `branch-B` into `main` (this will cause a conflict):  
   ```bash
   git merge branch-B
   ```
   ↦ merge branch-B with main ,this will give conflict
5. Resolve the conflict manually in `README.md`, then: 
   ↦ the conflict will resolve manually by opening readme file here conflict will show , resolve conflict as your reqirement .
   ```bash
   git add README.md
   git commit -m "Resolved merge conflict between branch-A and branch-B"
   ```
   ↦ then add readme file to staging area and commit the change

#### **Task 9: Renaming and Deleting Branches**
1. Rename a branch:  
   ```bash
   git branch -m old-branch-name new-branch-name
   ```
   ↦ to change name of branch
2. Delete a branch:  
   ```bash
   git branch -d feature-login
   ```
   ↦ to delete branch
---

### **Part 3: Advanced Git Operations**

#### **Task 10: Using Git Stash**
**[youtube video link for stash](https://youtu.be/HlnxA_0Pjwk?si=1Keh79IiYV91CRT-)**

↦ the repository has temp.md file (from local make file , add to staging area , commit the change and push)

1. Make changes to a file but don’t commit:  
   ```bash
   echo "Temporary work" >> temp.md
   ```
   ↦ editing file temp.md

2. Stash the changes:  
   ```bash
   git stash
   ```
   ↦ (stash = store (something) safely in a hidden or secret place) stash the uncommited changes ( save  your un-committed changes hinddenly  ) 
   ↦ locally any change in file will be hide 

3. View stashed changes:  
   ```bash
   git stash list
   ```
   ↦ show the list of all the stashes (list of stack of stash)
   example: ` stash@{0} `

4. Apply the stashed changes:  
   ```bash
   git stash apply
   ```
   ↦ apply the stash changes back to your local 

5. Drop the stash after applying:  
   ```bash
   git stash drop
   ```
   ↦ Once you have applied the stashed changes, you may want to remove the stash entry from your stash list


#### **Task 11: Rewriting History with Interactive Rebase**
1. Create multiple commits:  
   ```bash
   echo "Commit 1" > file1.txt && git add file1.txt && git commit -m "Commit 1"
   echo "Commit 2" > file2.txt && git add file2.txt && git commit -m "Commit 2"
   echo "Commit 3" > file3.txt && git add file3.txt && git commit -m "Commit 3"
   ```
   ↦
2. Squash commits into one:  
   ```bash
   git rebase -i HEAD~3
   ```
   Example: Replace `pick` with `squash` for the second and third commits.

#### **Task 12: Cherry-Picking Commits**
↦ initialy main branch , we amde secound branch namr new, now commiting some change , after that creating new branch
1. Create a new branch:  
   ```bash
   git checkout -b cherry-pick-example
   ```
   ↦creating new branch and swithing branch to it.

2. Cherry-pick a specific commit from another branch:  
   ```bash
   git cherry-pick <commit-hash>
   ```

   ↦ now we want content of one commit from main branch, then use git cherry-pick to store the commited change in branch new.

#### **Task 13: Tagging Commits**

1. Tag the current commit:  
   ```bash
   git tag -a v1.0 -m "Version 1.0 release"
   ```
   ↦ here tag is important bookmark which is easily reference sepecific versions.
   ↦ -a refer to annotated tag (store extra metadata such as author name, release notes, tag-message, and date )
   ↦ v1.0 = tage name 
   ↦ -m "----" = message describing the tag
   
2. Push the tag to the remote repository:  
   ```bash
   git push origin v1.0
   ```
   ↦ to push the tag to repo

#### **Task 14: Working with Remote Repositories**

1. Add a remote repository:  
   ```bash
   git remote add origin <repository-url>
   ```
   ↦ git remote add = to add a new remote repository to your local Git configuration

   ↦ origin = to refer to the main remote repository.

   ↦ `<repository-url>` = URL of the remote repository where you want to push your code

2. Push your changes to the remote repository:  
   ```bash
   git push origin main
   ```
   ↦ git push = to push data to repo.

   ↦ main = branch name


#### **Task 15: Forking and Contributing**

1. Fork a repository on GitHub.  
   ↦ go to the repository you want to fork.

   ↦ click the "Fork" button at the top right corner of the repository page

   ↦ the forked repository will be created under your GitHub account.

2. Clone the fork locally:  
   ```bash
   git clone <forked-repo-url>
   ```
   ↦ ` git clone ` = to create local copy of repo

   ↦ ` <forked-repo-url> ` = URL of forked repo
   
3. Create a new branch, make changes, and push:  
   ```bash
   git checkout -b fix-typo
   echo "Typo fixed" >> README.md
   git add README.md
   git commit -m "Fixed a typo"
   git push origin fix-typo
   ```
   ↦ making new branch and switching
   
   ↦ making file with some text
   
   ↦ adding to staging area
   
   ↦ commit the change
   
   ↦ push branch fix-typo to repo

4. Open a pull request on GitHub.  

   ↦Go to your forked repository on GitHub.

   ↦ Click the "New pull request" button.

   ↦ Select the original repository and the branch you created (fix-typo) as the source.
   
   ↦ Click the "Create pull request" button.
---

### **Part 4: Additional Practice**

#### **Task 16: Simulate Team Collaboration**
1. Create a repository and share it with a friend.  
   ↦ 
   ↦
   ↦
   ↦
   ↦
   ↦
2. Both make changes to the same file simultaneously.  
   ↦
   ↦
   ↦
   ↦
   ↦
3. Practice resolving merge conflicts and pushing changes.
   ↦
   ↦
   ↦
   ↦
   ↦
   ↦

#### **Task 17: Git Ignore**
1. Create a `.gitignore` file:  
   ```bash
   echo "node_modules/" > .gitignore
   ```
   ↦ making new file with some content

2. Add files and ensure ignored files are not staged:  
   ```bash
   git add .
   ```
   ↦ adding all data of the folder to staging area


