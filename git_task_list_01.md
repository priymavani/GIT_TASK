

## Part 1: Introduction to Version Control and Git

### **Task 1: Install and Configure Git**
1. Configure Git with your username and email 
    ```bash
    git config --globle user.name "priymavani"
    git config --globle user.email "priymavani@gmail.com"  
    ``` 
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
   ↦
   Example Output:  
   ```
   * 2f8d6a2 (HEAD -> main) Updated README with a description
   * d3c4b21 Initial commit: Added README.md
   ```