
### **Part 1: Git Basics**

#### **Task 1: Install and Configure Git**
1. Install Git from [git-scm.com](https://git-scm.com/).  
2. Configure your global Git settings:  
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your-email@example.com"
   ```

    ↦ download git application

    ↦ to link github account to local (globally) by user name and email
    
    

3. Verify the configuration:  
   ```bash
   git config --list
   ```
   ↦ to show detail of configuration variable(user.name , user.email) and value
   

#### **Task 2: Initialize a Repository**
1. Create a directory and initialize it as a Git repository:  
   ```bash
   mkdir MyProject
   cd MyProject
   git init
   ```
   ↦ mkdir to make folder 
   ↦ cd to navigate into folder
   ↦ to initilize folder (make folder ready to connect with repo)
   

   - **Purpose**: Initializes a `.git` folder to track changes.

---

### **Part 2: Basic Workflow**

#### **Task 3: Creating and Committing Files**
1. Create a file:  
   ```bash
   echo "Hello Git" > file1.txt
   ```
   ↦ to make file or change file content by "content to write or edit"

2. Stage and commit the file:  
   ```bash
   git add file1.txt
   git commit -m "Initial commit: Added file1.txt"
   ```
    ↦ to add file to staging area ( stores information about what will go into your next commit)

    ↦  commite the added file to save change (save point)

#### **Task 4: Viewing Changes**
1. Modify the file:  
   ```bash
   echo "Git is awesome!" >> file1.txt
   ```
   ↦ edit the file content

2. Check file status and differences:  
   ```bash
   git status
   git diff
   ```
   ↦status to check the   which changes have been staged, which haven't, and which files are not being tracked

   ↦ diff = Show changes between commits.


#### **Task 5: Undoing Changes**
1. Unstage a staged file:  
   ```bash
   git reset file1.txt
   ```
   ↦ to unstage a file that has been added to the staging area (index)

2. Discard uncommitted changes:  
   ```bash
   git checkout -- file1.txt
   ```
    ↦  any modifications you made to file1.txt since the last commit will be lost
---

### **Part 3: Branching and Merging**

#### **Task 6: Branch Management**
1. Create a branch and switch to it:  
   ```bash
   git checkout -b feature-branch
   ```
   ↦ making new branch and switing to it

2. List branches:  
   ```bash
   git branch
   ```
   ↦ to show list of branch (total branch)
3. Rename a branch:  
   ```bash
   git branch -m feature-branch feature-enhanced
   ```
   ↦ remane the branch by -m 

#### **Task 7: Merging Branches**
1. Merge `feature-enhanced` into `main`:  
   ```bash
   git checkout main
   git merge feature-enhanced
   ```
   ↦

#### **Task 8: Handling Merge Conflicts**
1. Create two conflicting branches and resolve a conflict manually:  
   ```bash
   git merge <branch-name>
   ```
   
2. Use:  
   ```bash
   git add <resolved-file>
   git commit
   ```
    ```bash
        # Create a new repository
        mkdir conflict-demo
        cd conflict-demo
        git init

        # Create an initial commit
        echo "This is a line." > file.txt
        git add file.txt
        git commit -m "Initial commit"

        # Create and switch to the first branch
        git checkout -b branch1
        echo "This line is added in branch1." >> file.txt
        git add file.txt
        git commit -m "Add line in branch1"

        # Create and switch to the second branch
        git checkout main
        git checkout -b branch2
        echo "This line is added in branch2." >> file.txt
        git add file.txt
        git commit -m "Add line in branch2"

        # Merge branch1 into branch2
        git checkout branch2
        git merge branch1

        # Manually resolve the conflict in file.txt
        # (edit the file to resolve the conflict)

        # Stage the resolved file
        git add file.txt

        # Commit the merge
        git commit -m "Resolved merge conflict between branch1 and branch2"
    ```

---

### **Part 4: Remote Repositories**

#### **Task 9: Remote Setup**
1. Add a remote repository:  
   ```bash
   git remote add origin https://github.com/your-username/repo.git
   ```
   ↦ git remote add = to add a new remote repository to your local Git configuration

   ↦ origin = to refer to the main remote repository.

   ↦ ` <repository-url> ` = URL of the remote repository where you want to push your code

2. Verify the remote:  
   ```bash
   git remote -v
   ```
   ↦ to verify that the remote repo has been added correctly 

   ```bash
   // output
   origin  https://github.com/priymavani/practice_git_github.git (fetch)
   origin  https://github.com/priymavani/practice_git_github.git (push)
   ```


#### **Task 10: Push and Pull**
↦ making a file ,adding it to staging area and commit the change .
1. Push changes to the remote repository:  
   ```bash
   git push -u origin main
   ```
   ↦ push the branch(main) to repo

   ↦ -u = puse and pull set defalut to this branch (main)

2. Pull changes from the remote:  
   ```bash
   git pull origin main
   ```
   ↦ featch changes from repo to your current branch in local

#### **Task 11: Cloning a Repository**
1. Clone a remote repository:  
   ```bash
   git clone https://github.com/your-username/repo.git
   ```
   ↦ ` git clone ` = to create local copy of repo

   ↦ ` <forked-repo-url> ` = URL of forked repo
   
---

### **Part 5: Advanced Git**

#### **Task 12: Stashing Changes**
1. Save uncommitted changes:  
   ```bash
   git stash
   ```
  ↦ (stash = store (something) safely in a hidden or secret place) stash the uncommited changes ( save  your un-committed changes hinddenly  ) 

  ↦ locally any change in file will be hide

2. Apply stashed changes:  
   ```bash
   git stash apply
   ```
   ↦ apply the stash changes back to your local 

3. Drop the stash:  
   ```bash
   git stash drop
   ```
   ↦ Once you have applied the stashed changes, you may want to remove the stash entry from your stash list

#### **Task 13: Tagging Commits**
1. Create and annotate a tag:  
   ```bash
   git tag -a v1.0 -m "Version 1.0 release"
   ```
    ↦ here tag is important bookmark which is easily reference sepecific versions.

   ↦ -a refer to annotated tag (store extra metadata such as author name, release notes, tag-message, and date )

   ↦ v1.0 = tage name 

   ↦ -m "----" = message describing the tag

2. Push the tag to the remote:  
   ```bash
   git push origin v1.0
   ```
   ↦ to push the tag to repo

#### **Task 14: Rewriting Commit History**
1. Use interactive rebase to modify commit messages:  
   ```bash
   git rebase -i HEAD~3
   ```
   - Replace `pick` with `edit` or `squash` as needed.

#### **Task 15: Cherry-Picking Commits**

    ↦ initialy main branch , we amde secound branch namr new, now commiting some change , after that creating new branch and switch to it.

1. Apply a specific commit to another branch:  
   ```bash
   git cherry-pick <commit-hash>
   ```
    ↦ now we want content of one commit from main branch, then use git cherry-pick to store the commited change in branch new.

---

### **Part 6: Collaboration**

#### **Task 16: Forking and Pull Requests**
1. Fork a repository and clone it locally:  
   ```bash
   git clone https://github.com/your-username/forked-repo.git
   ```
   ↦ goto the repo 

   ↦ click on the flrk button
   
   ↦ to clone in local ,git clone <URl>

   ↦ run git bash

2. Make changes and push them:  
   ```bash
   git checkout -b fix-typo
   echo "Typo fixed" >> README.md
   git commit -m "Fixed a typo"
   git push origin fix-typo
   ```
   ↦ making new branch and switch to it

   ↦ edit the content of file and add to staging area

   ↦ commit the change

   ↦ push branch to repo
   
3. Open a pull request on GitHub.
   
   ↦ navigate to forked repo

   ↦ switch from main to fix-typo

   ↦ create pull request

   ↦ with title and description

#### **Task 17: Simulating Team Collaboration**
1. Simulate a conflict by having two users modify the same file.  
2. Practice resolving the conflict as a team.

---

### **Part 7: Ignoring Files**

#### **Task 18: Using .gitignore**
1. Create a `.gitignore` file:  
   ```bash
   echo "node_modules/" > .gitignore
   git add .gitignore
   git commit -m "Added .gitignore"
   ```
   ↦ create file .gitingnore with some content

   ↦ add the file to staging area

   ↦ commit th change

2. Verify that ignored files are not staged:  
   ```bash
   git status
   ```
   ↦ by git status we see the file is not in staging area therfore the file is ingnor

---

### **Part 8: Automation and Cleanup**

#### **Task 19: Cleaning the Repository**
1. Remove untracked files:  
   ```bash
   git clean -f
   ```
   **[video for git clean](https://youtu.be/W_vXhT2YfBY?si=gawmjMLoAjlIGdOD)**

   ↦ git clean the file which are not in staging area are remove. 
   ↦ -n    = to check which files will be removed

   ↦ -n -d = to check which file and folder will be remove

   ↦ -f    = to delete file which are not tracked

   ↦ -d -f = to delete folder which are not tracked


#### **Task 20: Aliases and Shortcuts**
1. Create an alias for frequently used commands:  
   ```bash
   git config --global alias.st status
   git config --global alias.cm commit
   ```
   ↦ creating short-cut for any command (globally)

   ↦ making shortcut git st = git status

   ↦ making shortcut git cm = git commit

   * ↦ vim ~/.gitconfig to get list of shortcut made
2. Use the alias:  
   ```bash
   git st
   git cm -m "Message"
   ```
   ↦ using the shortcut of st = status and cm = commit.

---