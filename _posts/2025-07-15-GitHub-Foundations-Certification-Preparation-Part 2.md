---
title: GitHub Foundations Certification Preparation- Part 2
date: 2025-07-15 7:25
categories: [GitHub Foundations Certification Series]
tags: [GitHub]
---

Welcome back to the second part of my GitHub Foundations Exam Preparation Series! 
In **Part 1**, I covered the basics of Git, version control, and some essential Git commands.

In this part, I’ll walk you through the second course from the **GitHub Foundations Skill Track** on **DataCamp**, called **"Intermediate Git"**. This course builds on the basics and introduces more powerful Git features.

### Chapter 1: Working with branches

#### Introduction to branches

Let’s say you’re developing a new feature or fixing a bug — but you don’t want to mess up your main code.  
That’s where **branches** come in!

A **branch** is like a separate workspace where you can make changes, test ideas, or fix issues **without affecting the main branch** (usually called `main` or `master`).

Once everything works well, you can **merge** your branch back into the main code.  

The **default branch** in Git is usually called `main`. This is where we store the **working version** of our application — the stable code that is ready to use or deploy.

**To see all branches in your repository, use:**

```
git branch

```
This command shows a list of all branches.
The branch with a * before its name is your current working branch.

**Example output:**

```
  main
* feature-login
  bugfix-speed

```
In this example, you're currently working on the feature-login branch.

**Creating a New Branch**

To create a new branch (but stay in the current one):

```
git branch new_branch_name

```
This only creates the branch, it doesn't switch to it.

**Switching to a Branch**
To switch to a different branch:

```
git switch new_branch_name

```

Now you’re working inside that branch. Any changes you make will only affect this branch.

**Create and Switch in One Step**
You can also create a new branch and switch to it immediately with:

```
git switch -c new_branch_name

```
This is a shortcut for creating and switching in one line.

#### Modifying and comparing branches

**Comparing Branches in Git**

We use `git diff` not only to compare commits, but also to **compare two branches**.

To compare the differences between two branches:

```
git diff new_branch old_branch

```
This shows what is different in new_branch compared to old_branch.
Use this to see what changes haven’t been merged yet.

Note: When the output is long, Git uses a pager.

- Press the spacebar to scroll
- Press q to exit the view

**Renaming a Branch**
You can rename a branch using:

```
git branch -m old_name new_name

```
If you're already on the branch, just use:

```
git branch -m new_name

```
**Deleting a Branch**

To delete a branch that has been merged:

```
git branch -d branch_name

```
Git checks if the branch is safe to delete.

If the branch has not been merged, you’ll get an error.
**To force delete it anyway:**

```
git branch -D branch_name

```
Be careful! This will delete the branch even if it has unmerged changes.

#### Merging branches

Each Git branch should have a **specific purpose**, such as:

- Developing a new feature  
- Fixing a bug or debugging an error  
- Testing something without affecting the main project

This keeps your project clean, organized, and safe.

When you’re done working in a branch, you can **merge** it into another branch to bring in your changes.

#####  Merge Workflow

**Step 1: Identify the branches**

- **Source**: the branch you want to merge **from**  
- **Destination**: the branch you want to merge **into**

**Step 2: Switch to the destination branch**

For example, if you're merging changes into `main`:

```
git switch main

```

**Step 3: Merge the source branch**

```
git merge feature-branch

```
This merges the **feature-branch** into main.

**Merging from Another Branch**
You can also run this from a different branch:

```
git merge source destination

```
Let’s move on to the next topic: **Collaborating using Git**.  

### Chpater 2: Collaborating using git 

#### Merge Conflict: 

A **merge conflict** happens when Git is **unable to automatically resolve differences** between two branches.

This usually happens when:

- The **same file** is edited in two different branches  
- You try to **merge the branches**, and  
- Git doesn’t know **which version** of the file to keep

Result: **Conflict!**

---

**How to Resolve a Merge Conflict**

1. **Git will mark the conflicted file**  
   Open the file to review the conflict markers (like `<<<<<<<`, `=======`, `>>>>>>>`).

2. **Open the file using a terminal text editor** (e.g., nano):

```
nano file_name.extension

```

**Edit the file**

- Keep the version you want
- Remove the conflict markers

**Save the file in nano**

- Press Ctrl + O to save
- Press Enter
- Press Ctrl + X to exit

**Finish the Merge**
After editing and saving the file, add it to staging:

```
git add file.md

```

Then complete the merge by committing:

```
git commit -m "Resolve merge conflict"

```
Your merge is now successful! 

#### Introudction to remote

A **local repo** is stored on your own computer.  
You use it to build and test your project locally.

A **remote repo** is stored in the cloud, usually on platforms like:

- GitHub  
- GitLab  
- Bitbucket  

This makes it easy to **back up your project** and **collaborate with others**, no matter where they are.

**Cloning a Repository**

To start working with a remote or local repo, you first **clone** it — this means creating a copy on your own computer.

**Clone from a remote (like GitHub):**

```
git clone https://github.com/username/repo-name.git

```
**Clone from a local directory:**

```
git clone /home/sawrab/repo

```

**Clone from a local path and rename the folder:**

```
git clone /home/sawrab/repo new_repo

```

Now your project is on your local machine!

**Git and Remotes**

- When you clone a repo, Git will:
- Automatically remember where it came from
- Create a remote reference called origin

**List all remotes associated with your project:**

```
git remote

```

**See more details (URLs):**

```
git remote -v

```

**Add a New Remote**
You can add more remotes (e.g., to push the same project to another platform):

```
git remote add name URL

```
**Example:**

```
git remote add backup https://github.com/username/backup-repo.git

```

Now you can push and pull from both **origin** and **backup.**

#### Pulling from a Remote 

When you're working with a remote repository, you often need to get the latest changes made by others. This is called **pulling from a remote**.

**What does `git pull` do?**

- **`git pull`** is a combination of two commands: **`git fetch`** and **`git merge`**.  
  - It first **fetches** the changes from the remote repository.
  - Then, it **merges** those changes into your local branch.

**How to Pull from a Remote**

To pull the latest changes from a specific branch (e.g., `main`):

```
git pull origin main

```
`origin` is the default name for your remote repository.

`main` is the name of the branch you're pulling from.

**Important Notes Before Pulling**

- **Save your local work:** Before pulling, make sure to commit or stash your changes. Git may block the pull or cause conflicts if you have uncommitted work.
- **Merge Conflicts:** If the changes you're pulling conflict with your local changes, Git will prompt you to resolve the merge conflict manually.

#### Pushing to a Remote 

Once you've made changes locally and committed them, you may want to push those changes to the remote repository, so others can access and collaborate on your updates.

**What does git push do?**
`git push` uploads your local changes (commits) to the corresponding branch on the remote repository.

**How to Push to a Remote**
To push your local changes to the remote branch:

```
git push origin main

```

- `origin` is the remote repository where your code is stored (GitHub, GitLab, etc.).
- `main` is the branch you're pushing to.

**Important Notes Before Pushing**

- Commit your changes first: You must commit your changes locally before pushing.
- Upstream Branch: If your local branch is tracking a remote branch, you can simply use git push without specifying the remote and branch:

```
git push

```
**Summary of Commands**

**Pull latest changes from a remote branch:**

```
git pull origin main

```

**Push your local changes to the remote branch:**

```
git push origin main

```


**Simple push when the branch is already tracked:**

```
git push

```

Using git pull and git push helps you stay in sync with the remote repository and keep your local code up-to-date with other team members.

---

### Conclusion

In this part, we explored some powerful Git features that are super useful when working on real projects or collaborating with others.

We talked about:

- Creating, switching, and managing branches  
- Merging branches and resolving conflicts  
- Working with remote repositories  
- Pulling updates from remotes and pushing your changes

These are the tools you’ll use every day as a developer or contributor to open-source projects.

Stay tuned for **Part 3**, where we’ll dive into GitHub-specific workflows, pull requests, forks, and more collaboration tips to help you feel confident using GitHub in real-world scenarios.

Thanks for reading — see you in **Part 3**! 



