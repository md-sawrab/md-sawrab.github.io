---
title: GitHub Foundations Certification Preparation- Part 3
date: 2025-07-22 4:00
categories: [GitHub Foundations Certification Series]
tags: [GitHub]
---

---

Welcome to **Part 3** of my GitHub Foundations Exam Preparation Series. In **Part 1**, we explored the basics of Git and version control. In **Part 2**, we focused on working with branches, merging, and collaborating using Git.

Now, in **Part 3**, we’ll shift our focus to **GitHub** — the most popular platform for hosting and managing Git repositories online.

This part is based on the **"Introduction to GitHub"** course from the **GitHub Foundations Skill Track** on **DataCamp**.

### Chapter 1: Introduction to GitHub

#### What is GitHub 

**GitHub** is a **cloud-based hosting service** for Git repositories.  
It allows users to **store**, **share**, and **track** their work using version control.

GitHub is built on top of Git, so you get all of Git’s powerful tracking features — but now on the web!


**What Can You Use GitHub For?**

- **Storing your projects online**  
  So you can access them from anywhere

- **Tracking changes to your code**  
  Also known as **version control** — you can see who changed what and when

- **Collaborating with others**  
  GitHub makes it easy to work on the same project with your team, even from different locations


GitHub is the most popular platform for developers and open-source communities — it's where millions of projects live!


**Git vs GitHub**

People often think **Git** and **GitHub** are the same thing, but they’re not.

Here’s the difference:

**Git**

- Git is a **version control system**
- It runs **locally** on your computer
- It helps you **track changes** in your files over time
- You can **work offline** and manage versions without the internet

Example: `git init`, `git commit`, `git push`, etc.

**GitHub**

- GitHub is a **cloud-based platform**
- It **enhances Git** by providing a web interface
- It lets you **store your Git repositories online**
- It makes **collaboration easier** (with tools like pull requests, issues, forks, etc.)

**GitHub Repository**

A **GitHub repository** contains **all the files** of a project and also **records the past versions** of those files using Git.

It acts as a **backup** of your project in the cloud and is often referred to as a **remote repository**.

You can push changes to it, pull updates from it, and collaborate with others easily.

#### Seeting Up a Repo

**Creating a Repository on GitHub**

1. Go to [github.com](https://github.com)
2. Click the **"New"** button under the Repositories tab
3. Enter a **repository name**
4. Choose visibility:  
   - **Public** (anyone can see it)  
   - **Private** (only you and invited people can see it)
5. Click **Create repository**

**Key Components of a GitHub Repo**

**`README.md`**

- A **README file** is a Markdown file shown at the top of your repo.
- It usually explains:
  - What the project is about  
  - How to use it  
  - Installation steps or links

> Think of it like a homepage or instruction manual for your project.

**`.gitignore`**

- This file tells Git which files or folders to **ignore** (not track).
- Example: temporary files, log files, build folders, API keys
- You can think of it like a "**blocked list**" — it keeps certain files out of version control.

**Issues**

- **Issues** are where you **track bugs, tasks, or ideas**
- Team members and contributors can:
  - Report problems  
  - Ask questions  
  - Suggest improvements
- It’s like a built-in to-do list with comment threads!

** Pull Requests (PR)**

- A **Pull Request** is a **request to make changes** to the codebase.
- Common in team projects or open-source work.
- You propose a change (from your branch), and someone reviews it before merging it into the main branch.
- GitHub makes it easy to comment, suggest changes, and collaborate on the code.

#### Creating a `README.md` File

A `README.md` file is usually the **first file** you add to your GitHub repository.  
It helps others understand your project, how to use it, and how to contribute.

---

**How to Create a README**

**Option 1: On GitHub (Recommended for Beginners)**

1. After creating a new repository on GitHub, you’ll see an option:
   >  Add a README file

2. Check that box before clicking **"Create repository"**.

3. GitHub will automatically create a basic `README.md` file for you.

4. You can then click the file, then click **"Edit"** (pencil icon) to update it.

**Option 2: On Your Local Computer**

1. In your project folder, create a new file named:

```
README.md

```

### Chapter 2: Working with Repos

#### Modifying a repo structure 

Once you've created a GitHub repo, you can start **adding files**, **creating folders**, and **working with branches**.

**Adding Files to the Repo**

You can easily add files to your GitHub repository directly from the website:

1. Go to your repository
2. Click the **"Add file"** button
3. Choose **"Create new file"**
4. Enter the **file name** (like `README.md`)
5. Add your content
6. Scroll down and **commit** the changes (write a short message and click **Commit new file**)

Done! Your file is now part of your repo.

---

**Creating Folders (Directories)**

GitHub **doesn’t allow empty folders**, so you must include at least one file inside.

**To create a folder structure:**

repo_name/directory_name/README.md

#### Working with Branches

Branches allow you to work on different parts of a project at the same time — without changing the main code.

**Why use branches?**

- Develop new features without breaking the main version
- Fix bugs independently
- Test out ideas safely

**Default Branch**: When you create a new repository, GitHub sets the default branch to main
This is usually where your stable, working code lives

**Branch Protection Rules**

To maintain code quality and prevent unauthorized changes, we have implemented branch protection rules for critical branches (e.g., `main`).

Rules for Specific Branch

- **Require Pull Request Before Merge**  
  All changes must be made via pull requests to ensure proper review and traceability.

- **Require Pull Request Approval Before Merge**  
  At least one team member must approve the pull request before it can be merged. This promotes collaborative review and minimizes the risk of bugs or vulnerabilities.

#### Repository Access

Access to this repository is intentionally restricted due to the nature of its content and purpose.

1. **Sensitive Dataset Usage**
This repository contains datasets that may include **personal or identifiable information** (e.g., names, emails, demographic data).  

2. **Commercial Product Development**
The codebase is part of a **commercial product** currently under development or use.  

#### Personal Access Tokens

GitHub no longer supports account password authentication for Git operations via HTTPS.  
Instead, **Personal Access Tokens (PATs)** are used as a secure way to authenticate when working from the terminal.

**Use Case: Git in the Terminal**

You can use Git in the terminal to interact with your GitHub repositories by authenticating with a PAT.

**How to Authenticate**

1. **Generate a PAT**  
   - Go to your GitHub account:  
     `Settings` > `Developer settings` > `Personal access tokens` > `Tokens (classic)`
   - Click **"Generate new token"** and select scopes (e.g., `repo`, `workflow`).
   - Copy and save the token securely.

2. **Use in Terminal (HTTPS)**  
   When prompted for your GitHub password during a Git operation (e.g., `git push`),  
   enter your **Personal Access Token** instead of your password.

```
   git clone https://github.com/username/repo.git
   git add .
   git commit -m "Your message"
   git push origin main

```

### Chapter 3: Collaboration with GitHub

#### Using others repo

When you want to use or contribute to someone else's repository, you typically **clone** or **fork** it depending on your purpose.

**Cloning a Repository**

Cloning is like making a **copy-paste** of a project — but with a live link to the original.

**What Happens When You Clone?**

- Creates a **local copy** of the repository on your computer.
- Maintains a **connection to the original repository** (called `origin`).
- You can **pull changes** from the original to stay updated.
- With proper access, you can **push changes back** to the original repository.

**Example:**
```
git clone https://github.com/original-owner/repo-name.git

```
**Forking a Repository**

Forking creates a **copy of the repository under your own GitHub account**, but it's **not directly linked** to the original for pushing.

**How Forking Works**

- Used when you don’t have permission to push to the original repository.
- You can **clone your fork** locally, make changes, and push to **your own fork**.
- Then, you can submit a **pull request** to suggest changes to the original repository.

**Clone vs Fork**

| Feature                 | Clone                            | Fork                               |
|-------------------------|----------------------------------|------------------------------------|
| Connection to Original  | Yes (`origin` remote)            | No direct push access              |
| Where it lives          | On your local machine            | On your GitHub account             |
| Use Case                | You have push access             | For contributing to someone else’s repo |
| Can Push Back?          | Yes (if access is granted)       | No (you create a pull request)     |
| Good for Updates?       | Yes, via `git pull`              | Requires setting up remote to sync |

#### GitHub Issues

Another part of effective collaboration is **communicating through issues**. Issues act as a way to plan, track, and discuss work.

**Messages in Issues Help To:**
- Track problem fixes 
- Plan upcoming features or improvements 
- Assign and follow up on important tasks 
- Communicate between team members 

**Key Features:**
- **Assign** — designate who should work on the issue.
- **Tag** — mention or label people who need to read or respond to the issue.

---

#### Pull Requests (PRs)

Pull Requests are a way to:
- Notify others about changes.
- Allow the repository owner or collaborators to review changes before merging.
- Follow best practices by proposing changes from a **feature branch** rather than the `main` branch.
- Merge two branches once the changes are approved and ready.

**Terminology:**
- **Base branch** – the branch we want to update (e.g., `main`).
- **Compare branch** – the branch that contains our proposed changes.

---

**Reviewing Pull Requests**

- **Assignee** — the person responsible for working on or merging the pull request.
- **Reviewer** — team members who look over the code, suggest improvements, and **approve the PR** if everything looks good.

>  A successful PR ends with a clean **merge** of the compare branch into the base branch.

### Conclusion

In this part, we explored the basics of **GitHub** — how it's different from Git, how to create and manage repositories, and some useful features like `README.md`, `.gitignore`, issues, and pull requests.

We also learned how GitHub makes collaboration easy by letting you host your projects in the cloud, track tasks, and work with branches.

Understanding these core GitHub features is essential if you want to contribute to open-source projects or work on team-based software development.

Thanks for reading — see you in **Part 4**! 


