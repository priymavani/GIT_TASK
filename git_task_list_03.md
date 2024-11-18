
### **Task List: Focused on Repository Management, Commits, Branching, and Merging**

### **Part 1: Creating and Cloning Repositories**

#### **Task 1: Create a Local Git Repository**
1. Create a new project folder:  
   ```bash
   mkdir MyProject
   cd MyProject
   ```
   ↦ creating new folder 

   ↦ navigate to the folder

2. Initialize it as a Git repository:  
   ```bash
   git init
   ```
   ↦ to initilize folder (make folder ready to connect with repo)

   - **Explanation**: This creates a `.git` folder that stores the repository's metadata and history.

3. Verify the repository status:  
   ```bash
   git status
   ```
   ↦ to know the file is in staging area and know on which branch we are

   - **Example Output**:  
     ```
     On branch main
     No commits yet
     nothing to commit (create/copy files and use "git add" to track)
     ```

#### **Task 2: Clone a Remote Repository**
1. Clone a GitHub repository:  
   ```bash
   git clone https://github.com/username/repo.git
   ```
   ↦ to clone github repo into local folder 

   - **Explanation**: This command downloads the repository to your local system.  

2. Verify the cloned repository structure:  
   ```bash
   cd repo
   ls -a
   ```
   ↦ navigate to folder repo

   ↦ ls -a = list all files in current folder include hidden files

   - **Output**: The `.git` folder should be present.

---

### **Part 2: Understanding Commits and Commit Messages**

#### **Task 3: Commit Changes Locally**
1. Create a new file and add content:  
   ```bash
   echo "Welcome to Git" > README.md
   ```
   ↦ creating new file with some content

2. Stage the file:  
   ```bash
   git add README.md
   ```
   ↦ file is adding to staging area

   - **Explanation**: `git add` moves changes to the staging area.

3. Commit the staged file:  
   ```bash
   git commit -m "Initial commit: Added README.md"
   ```
   ↦ commit the change 

   - **Explanation**: Commits save the current state of the repository with a message describing the change.

#### **Task 4: Write Effective Commit Messages**
1. Create a detailed commit message:  
   ```bash
   git commit -m "Added initial version of README.md with project overview"
   ```

    ↦ Commits save the current state of the repository with a message describing the change.

   - **Explanation**: Commit messages should follow conventions such as starting with a capital letter, being concise, and using the imperative mood.

2. Commit multiple files with one message:  
   ```bash
   touch file1.txt file2.txt
   git add .
   git commit -m "Added two new files for feature setup"
   ```
   ↦ making empty file with touch command

   ↦ adding to staging area

   ↦ Commits save the current state of the repository with a message describing the change.


---

### **Part 3: Viewing Commit History with `git log`**

#### **Task 5: View Detailed Commit History**
1. View full commit logs:  
   ```bash
   git log
   ```

   ↦ history of commit

   - **Explanation**: Shows a detailed list of commits with hash, author, date, and message.

2. View commit history in a compact format:  
   ```bash
   git log --oneline
   ```
   ↦ --oneline = command to show each commit on a single line

   - **Example Output**:  
     ```
     e23d8a7 Added initial version of README.md
     f7b3c62 Initial commit: Added README.md
     ```

#### **Task 6: Customize Log Outputs**
1. View logs with a graphical representation:  
   ```bash
   git log --oneline --graph --decorate
   ```
2. Filter logs for a specific file:  
   ```bash
   git log README.md
   ```
   ↦ to visualize the commit history in a graphical format. This is especially useful for understanding the branching and merging structure of your repository. 

---

### **Part 4: Understanding Branching and Merging**

#### **Task 7: Understanding Branching**
1. List all branches:  
   ```bash
   git branch
   ```
   ↦ to get list of all branch 

   - **Explanation**: Displays the current branch and all other branches.

2. Create a new branch:  
   ```bash
   git branch feature-branch
   ```
   ↦ creating new branch

   - **Explanation**: Creates a new branch without switching to it.

3. Switch to the new branch:  
   ```bash
   git checkout feature-branch
   ```
   ↦ switing to the current branch to new branch

   - **Alternative Command**:  
     ```bash
     git checkout -b feature-branch
     ```
     ↦ direct make new branch and switch to it

     - **Explanation**: Creates and switches to the branch in one command.

---

### **Part 5: Creating and Working with Branches**

#### **Task 8: Make Changes in a Branch**
1. Add content to a file in the new branch:  
   ```bash
   echo "Feature in progress" > feature.txt
   git add feature.txt
   git commit -m "Added feature.txt in feature-branch"
   ```
   ↦ **single > :**
      If feature.txt does not exist, it will be created.<br>
      If feature.txt exists, it will be replaced with the  new content.

   ↦ **double >> :**
      If feature.txt does not exist, it will be created.<br>
      If feature.txt exists, the new content will be added after the existing content.

    ↦ adding to staging area and commite the change

#### **Task 9: Merging Branches**
1. Switch back to the `main` branch:  
   ```bash
   git checkout main
   ```
   ↦ switching to main branch

2. Merge the `feature-branch` into `main`:  
   ```bash
   git merge feature-branch
   ```
   ↦ merging current branch to feature-branch

   - **Explanation**: Combines the changes from `feature-branch` into `main`.

---

### **Part 6: Resolving Merge Conflicts**

#### **Task 10: Simulate a Merge Conflict**

 ↦ making file conflict.txt and making new branch

1. Modify the same line in a file on two branches:  
   ```bash
   echo "Main branch content" > conflict.txt
   git add conflict.txt
   git commit -m "Added conflict.txt in main branch"
   ```
   ↦ adding content to file , adding to staging area and commit the change

2. Switch to the other branch and make conflicting changes:  
   ```bash
   git checkout feature-branch
   echo "Feature branch content" > conflict.txt
   git add conflict.txt
   git commit -m "Modified conflict.txt in feature-branch"
   ```
   ↦ switching to new branch , adding content to file , adding to staging area and commit the change

3. Merge `feature-branch` into `main`:  
   ```bash
   git checkout main
   git merge feature-branch
   ```
   ↦ switching to main branch and merging new branch with current branch .

4. Resolve the conflict by editing the file and choosing the correct version:  
   - Open `conflict.txt` and decide which changes to keep.
   - Stage the resolved file:  
     ```bash
     git add conflict.txt
     ```
   - Commit the merge:  
     ```bash
     git commit -m "Resolved conflict in conflict.txt"
     ```

    ↦ conflict occur , resolving conflict by opening file ,adding resolved file to staging area and commit the change

---

### **Part 7: Deleting and Renaming Branches**

#### **Task 11: Delete a Branch**
1. Delete a local branch:  
   ```bash
   git branch -d feature-branch
   ```
   ↦ deleting branch by -d

   - **Explanation**: This deletes the branch only if it has been fully merged.  

2. Force-delete a branch:  
   ```bash
   git branch -D feature-branch
   ```
   ↦ deleting branch forcefully by -D

   - **Explanation**: Deletes the branch even if it hasn’t been merged.

#### **Task 12: Rename a Branch**
1. Rename the current branch:  
   ```bash
   git branch -m new-branch-name
   ```
   ↦ changing name of current branch

2. Rename another branch (not checked out):  
   ```bash
   git branch -m old-branch-name new-branch-name
   ```
   ↦ changing branch name by naming both branch first old branch and secound new branch

---

### **Consolidated Flow Summary**

1. Start by creating and cloning repositories.
2. Learn to commit changes effectively with clear messages.
3. Explore commit history using various `git log` commands.
4. Understand branching and practice creating, switching, and merging branches.
5. Dive into resolving merge conflicts.
6. End by managing branches through deletion and renaming.