
### **Task List: Focused on Advanced Git Operations**

### **Part 1: Understanding and Using `git stash`**

#### **Task 1: Save Changes Temporarily with `git stash`**
1. Make changes to a file without committing:  
   ```bash
   echo "Temporary changes" >> temp-file.txt
   ```
   ↦ making new file with some content

2. View the status of changes:  
   ```bash
   git status
   ```
   ↦ chaking status , which show temp-file.txt is not staged

   - **Output**:  
     ```
     Changes not staged for commit:
       modified:   temp-file.txt
     ```
     

3. Stash the changes:  
   ```bash
   git stash
   ```
   ↦ (stash = store (something) safely in a hidden or secret place) stash the uncommited changes ( save your un-committed changes hinddenly ) 

   ↦ locally any change in file will be hide

   - **Explanation**: This command saves changes to a stash and restores the working directory to the last commit state.

4. View the stashed changes:  
   ```bash
   git stash list
   ```
   ↦ show the list of all the stashes (list of stack of stash) example: stash@{0} 

   - **Output**:  
     ```
     stash@{0}: WIP on main: 27e5f23 Added temporary changes
     ```

#### **Task 2: Apply and Drop Stashed Changes**
1. Apply the most recent stash:  
   ```bash
   git stash apply
   ```
    ↦  apply the stash changes back to your local

2. Drop the most recent stash after applying it:  
   ```bash
   git stash drop
   ```
     ↦ Once you have applied the stashed changes, you may want to remove the stash entry from your stash list then drop it .

3. Alternatively, to apply a specific stash:  
   ```bash
   git stash apply stash@{1}
   ```
    ↦  apply the stash changes back to your local by git stash apply stash@{1} or git stash apply 1

#### **Task 3: Stash Untracked Files**
1. Stash changes, including untracked files:  
   ```bash
   git stash -u
   ```
    ↦ -u = includes untracked files in the stash.(files that have been created but not yet added to the Git index with git add)

2. Apply stashed changes including untracked files:  
   ```bash
   git stash apply
   ```
    ↦ 

---

### **Part 2: Rewriting History with `git rebase`**

#### **Task 4: Rebase Commits to a New Base**
1. Rebase the current branch onto `main`:  
   ```bash
   git rebase main
   ```
   - **Explanation**: This command applies the commits from your current branch on top of the latest commit from `main`.

2. Resolve any conflicts that may arise during rebase, and continue:  
   ```bash
   git rebase --continue
   ```

#### **Task 5: Canceling a Rebase**
1. If a rebase goes wrong, abort it:  
   ```bash
   git rebase --abort
   ```

---

### **Part 3: Interactive Rebase (`git rebase -i`)**

#### **Task 6: Use Interactive Rebase to Modify Commit History**
1. View the last few commits:  
   ```bash
   git log --oneline
   ```

2. Start an interactive rebase for the last 3 commits:  
   ```bash
   git rebase -i HEAD~3
   ```
   - **Explanation**: This opens an editor with the list of commits in the last 3 commits.

3. Modify the commits by changing `pick` to one of the following:
   - `squash` (combine commits)
   - `reword` (edit commit message)
   - `edit` (edit commit content)
   - `drop` (remove commit)

4. Example of squashing two commits:
   - Change the second commit from `pick` to `squash` and save.
   - Git will combine the commit messages for the squashed commit.

#### **Task 7: Complete Interactive Rebase**
1. After modifying the commits, save and close the editor.
2. Resolve any conflicts if prompted, then continue the rebase:  
   ```bash
   git rebase --continue
   ```

---

### **Part 4: Cherry-Picking Commits (`git cherry-pick`)**

#### **Task 8: Pick a Specific Commit**
1. View the commit history to find the commit hash you want to cherry-pick:  
   ```bash
   git log --oneline
   ```

2. Cherry-pick a specific commit by its hash:  
   ```bash
   git cherry-pick <commit-hash>
   ```
   - **Example**:  
     ```bash
     git cherry-pick e23d8a7
     ```

3. Resolve conflicts if any, then commit the changes:  
   ```bash
   git add .
   git cherry-pick --continue
   ```

---

### **Part 5: Tagging Commits (`git tag`)**

#### **Task 9: Tag a Commit**
1. Tag the current commit with a version number:  
   ```bash
   git tag -a v1.0 -m "Initial release"
   ```

2. List all tags:  
   ```bash
   git tag
   ```

#### **Task 10: Tag a Specific Commit**
1. Tag a specific commit by its hash:  
   ```bash
   git tag -a v1.1 <commit-hash> -m "Bug fix"
   ```

#### **Task 11: Push Tags to Remote**
1. Push a specific tag to the remote repository:  
   ```bash
   git push origin v1.0
   ```

2. Push all tags to the remote repository:  
   ```bash
   git push --tags
   ```

---

### **Part 6: Working with Remote Repositories**

#### **Task 12: Add a Remote Repository**
1. Add a remote repository URL to the project:  
   ```bash
   git remote add origin https://github.com/username/repo.git
   ```

#### **Task 13: Fetch Changes from Remote**
1. Fetch changes from the remote repository without merging them:  
   ```bash
   git fetch origin
   ```

2. View fetched branches:  
   ```bash
   git branch -r
   ```

#### **Task 14: Pull Changes from Remote**
1. Pull the latest changes from the remote repository and merge them into the local branch:  
   ```bash
   git pull origin main
   ```

#### **Task 15: Push Changes to Remote**
1. Push local changes to the remote repository:  
   ```bash
   git push origin main
   ```

2. Push a new branch to the remote repository:  
   ```bash
   git push origin feature-branch
   ```

#### **Task 16: Delete Remote Branch**
1. Delete a remote branch:  
   ```bash
   git push origin --delete feature-branch
   ```

---

### **Part 7: Forking and Contributing to Open-Source Projects**

#### **Task 17: Fork a Repository on GitHub**
1. Go to a repository on GitHub and click **Fork** in the top right corner to create your own copy of the repository.

2. Clone the forked repository to your local machine:  
   ```bash
   git clone https://github.com/your-username/repo.git
   ```

#### **Task 18: Make Changes and Commit**
1. Create a new branch for your changes:  
   ```bash
   git checkout -b fix-typo
   ```

2. Make changes to the code (e.g., fix a typo in `README.md`), stage, and commit them:  
   ```bash
   git add README.md
   git commit -m "Fixed typo in README.md"
   ```

#### **Task 19: Push Changes to Your Fork**
1. Push the changes to your remote fork:  
   ```bash
   git push origin fix-typo
   ```

#### **Task 20: Create a Pull Request**
1. Go to your forked repository on GitHub, click on **Compare & Pull Request**.
2. Write a description of your changes and submit the pull request to the original repository.

#### **Task 21: Sync Your Fork with the Original Repository**
1. Add the original repository as a remote source:  
   ```bash
   git remote add upstream https://github.com/original-owner/repo.git
   ```

2. Fetch changes from the original repository:  
   ```bash
   git fetch upstream
   ```

3. Merge changes from the original repository into your local branch:  
   ```bash
   git checkout main
   git merge upstream/main
   ```

4. Push the changes to your fork:  
   ```bash
   git push origin main
   ```

---

### **Consolidated Summary**

1. **Stashing**: Saving and applying uncommitted changes temporarily.
2. **Rewriting History**: Using `git rebase` and `interactive rebase` to modify and clean up commit history.
3. **Cherry-Picking**: Selecting specific commits from another branch.
4. **Tagging**: Labeling commits for versioning.
5. **Working with Remote Repositories**: Managing remotes, pushing, pulling, and fetching changes.
6. **Forking & Contributing**: Forking repositories, contributing to open-source projects, and syncing your fork.