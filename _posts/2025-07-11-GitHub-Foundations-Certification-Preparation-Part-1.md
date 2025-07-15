---
title: GitHub Foundations Certification Preparation- Part 1
date: 2025-07-11 6:15
categories: [GitHub Foundations Certification Series]
tags: [GitHub]
---

On June 26, I gave the **GitHub Foundations Certification** Exam, and Alhamdulillah, I passed! To get prepare for the exam, I used several resources. One of the best was the **GitHub Foundations Skill Track** on DataCamp. It has 4 courses that explain things clearly and also give hands-on practice. These helped me understand how to use GitHub in real life.

While preparing for the exam, I also made some handwritten notes to remember the important points. In this blog series, I will share what I learned from each of the 4 courses. This is Part 1, and I will start with the first course, nammed [**Introduction to Git**](https://app.datacamp.com/learn/courses/introduction-to-git).

### Chapter 1: Introduction to Git

#### Introduction to version control

Before we dive into Git, it's important to understand what version control is and why it's useful. **Version control** is a system that helps manage and track changes to files, programs, and directories. If something change or brack we can revert to an earlier version. For example, imagine you're working on a coding project. After making some changes, you realize something went wrong. With version control, you can easily go back to the version that was working perfectly - just like "undo" but smarter and for your whole project!

With version control, you can:

- Track files in different states
- Combine different versions of files
- Identify a specific version to fix errors or issues

One popular program for version control is **Git**. It is open source and scalable. Git commands are run in the **shell**, also known as the **terminal**.

Before running Git commands, it's good to know a few basic **terminal commands**. These help you move around your computer using the shell.

```
pwd   # Shows the current folder (Print Working Directory)
cd    # Changes the folder (Change Directory)
ls    # Lists all files and folders in the current location
cd ~  # Goes to the home directory
cd .. # Goes back to the parent directory (one level up)
```

A **directory** (often called a **folder**) is where your files are stored on your computer. In Git, we often work inside directories to track and manage project files.

**Git repository (repo)** is basically a **project folder** that Git is tracking. Git stores all of its extra information (like version history and settings) in a hidden folder called **`.git`** inside that project folder.

#### Creating a New Git Repository

To create a new Git repository, use the `git init` command. 

```
git init repo_name

```
This command creates a new folder named **repo_name** and sets it up as a Git repository by adding a hidden `.git` folder inside it. 

If you already have a folder and want to turn it into a Git repository, you can run `git init` **inside that folder**, without giving a name.

First, go to your folder using `cd`:

```
cd my_existing_folder

```
Then, run:

```
git init

```

You can check if it worked by running:

```
git status

```

#### Staging and committing files

**Git Workflow (Basic Steps)**

Here's a basic Git workflow you can follow when working on a project:

**Edit and Save**  
   Make changes to your files on your computer and save them.

**Add to Staging Area**  
   Use the `git add` command to tell Git which files you want to track and prepare for commit.

```
   git add filename        # add a specific file
   git add .               # add all changed files

```
**Commit the Changes**

Use the `git commit` command to save your changes with a message.


```
    git commit -m "Write a short message about the changes"

```

### Chapter 2: Version history

#### Viewing the version history

git stores data through commit. When we make commit, git take a snapshot.

A Git commit is made up of **three main parts**:

1. **Commit**  
   - Stores metadata like the author name, date, commit message, and reference to the previous commit.

2. **Tree**  
   - Keeps track of the file names and their locations (like a folder structure).

3. **Blob (Binary Large Object)**  
   - Stores the actual content of the files in a compressed format.  
   - It takes a snapshot of the file content at the time of the commit.

**Git Hashes**

Every commit in Git has a unique ID called a **hash**.  
This hash is a long string made using a mathematical formula (SHA-1). It looks something like this:

**e4bfb2a1e5a8b92a5ef45b39d5c69d7c4aabc123**


Git uses this hash to:

- Identify each commit uniquely  
- Keep track of the entire history of changes  
- Help prevent accidental changes or data loss  

You can see the commit hash by running:

```
git log

```
#### Version history tips and tricks

Customizing `git log` Output

The `git log` command shows the history of commits, and you can customize it in different ways:

- **Show the last 3 commits:**

```
  git log -3

```
**View commit history for a specific file:**

```
git log filename.txt

```

**Filter commits by date:**

```

git log --since="2024-07-01"

```

Finding and Viewing a Specific Commit in Git

To find and check the details of a specific commit, follow these steps:

1. **View the commit history** using:

```
git log

```
Copy the commit hash you want to explore. 

Use git show with the hash to view the full details of that commit:

```
git show e4bfb2a1e5a8b92a5ef45b39d5c69d7c4aabc123

```
This will display information such as:

- Author and date
- Commit message
- The actual changes made to the file(s)

#### Comparing versions

Git provides powerful commands to compare versions in your project.

 `git diff`: See the Differences Between Versions


**Compare the latest committed version with the **working directory** (not yet staged):**

```
git diff file.md  # file.md is just an example file name

```

Stage the file first:

```
git add file.md

```
**Compare the staged version with the last commit:**

```
git diff --staged file.md

```
**Compare all staged files with the last commit:**

```
git diff --staged

```
**Comparing Two Commits**

First, see your commit history:

```
git log

```

Then compare two commits using their hashes (place the most recent one last):

```
git diff <older-commit-hash> <newer-commit-hash>

```
**To compare the latest commit with the one before it:**

```
git diff HEAD~1 HEAD

```
**HEAD points to the latest commit.** HEAD~1 is one commit before that.

#### Restoring and Reverting Files

**Revert the repository to the previous commit and create a new commit:**

```

git revert HEAD

```

**Revert without opening a text editor:**

```
git revert --no-edit HEAD

```

**Revert without making an automatic commit:**

```
git revert -n HEAD

```

**Note: git revert works on commits, not individual files.**

**Revert a Single File to an Older Version**
Replace a file with the version from a previous commit:

```
git checkout HEAD~1 -- file.md

```

**Unstaging Files**
Check your current status:

```
git status

```

**Unstage a single file:**

```
git restore --staged file.md

```
**Unstage all staged files:**

```
git restore --staged

```

### Conclusion

In this part, we covered the basics of Git and version control — including how to create a repository, use basic terminal commands, understand commits, and compare changes using `git diff`, `git log`, and more.

These are the foundation of working with Git. If you're just getting started, practicing these commands will help you feel more confident.

In the next part, I’ll go deeper into the second course from the GitHub Foundations skill track and share more useful commands and tips.



Thanks for reading — see you in **Part 2**! 
