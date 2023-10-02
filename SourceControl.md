# Source Control: GitHub, Git and Gitflow  
  
## Table of Contents  
  
1. [Introduction to Source Control](#introduction-to-source-control-and-its-importance)  
2. [Using Git and GitHub for Source Control and External Hosting](#using-git-and-github-for-source-control-and-external-hosting)  
3. [Introduction to Git](#introduction-to-git)  
4. [Introduction to GitHub](#introduction-to-github)  
5. [Introduction to Gitflow](#introduction-to-gitflow)  
6. [Gitflow Branching Strategy Cheat Sheet](#gitflow-branching-strategy-cheat-sheet)  
7. [Key Gitflow Terms](#key-gitflow-terms)  
  
## Introduction to Source Control and Its Importance  
  
Source Control, also known as Version Control, is a system that records changes to a file or set of files over time so that you can recall specific versions later. It allows you to track modifications, see who made changes, when they made them, and why. This system is a critical tool for software developers, as it facilitates a controlled, organized system for making changes to code.  
  
The primary reasons for using source control include:  
  
1. **Collaboration**: Source control allows multiple developers to work on the same project without stepping on each other's toes. It manages modifications from multiple sources and merges them into a single codebase.  
  
2. **Versioning**: Source control systems keep a history of every change made to the codebase, allowing you to roll back changes, compare different versions, and find the source of bugs.  
  
3. **Backup**: In the case of an unexpected event like data loss or hardware failure, you can restore your codebase from the source control system.  
  
4. **Traceability**: It provides an audit trail for changes to the codebase. You can track when a specific change was introduced, by whom, and why.  
  
5. **Experimentation**: Developers can create separate branches to experiment with new features or ideas, without affecting the main codebase. If the experiment is successful, it can be merged into the main code. If not, it can be discarded without any impact.  
  
In essence, source control is a critical component of software development that improves team collaboration, provides a history of modifications, and creates an environment for safe experimentation.  
    
## Using Git and GitHub for Source Control and External Hosting  
  
Git and GitHub, while they sound similar, serve different but complementary roles in the world of software development. To fully understand their benefits, it's important to understand the difference between the two and why I recommend using both for source control and external hosting in your studies.  
  
**Git** is an open-source distributed version control system. It allows you to track changes you make in your code over time. If you make a mistake, you can turn back the clock and revert to earlier code without much hassle. Git is a tool that runs locally on your machine, providing a way to interact with the history of your codebase.  
  
**GitHub**, on the other hand, is a cloud-based platform where developers store their Git repositories online. It's a place where you can host and review code, manage projects, and build software alongside millions of other developers. GitHub takes what Git does on a local level and applies it to the cloud, providing a space where teams can collaborate and contribute to the same codebase without overwriting each other's changes.  
  
The primary difference between Git and GitHub lies in their functionality. Git is focused on version control and code sharing, while GitHub provides a broad platform for both collaborative and distributed version control. Meaning, while Git is a command-line tool, GitHub provides a web-based graphical interface. It also provides access control and several collaboration features, like wikis and basic task management tools for every project.  
  
Setting up and using Git and GitHub involves several steps:  
  
1. **Installing Git**: Download and install Git from [Git's website](https://git-scm.com/downloads). This will allow you to run Git from the command line.  
  
2. **Creating a GitHub account**: To create your own projects or contribute to others, you'll need to sign up for a free account on [GitHub's website](https://github.com/).  
  
3. **Creating a new repository**: On GitHub, you can create a new repository to host your project. This will serve as the project's home, where you and others can navigate files, open issues, and more.  
  
4. **Making changes and committing them**: With Git installed, you can clone the repository to your local machine, make changes, and then commit those changes using commands like `git add` and `git commit`.  
  
5. **Pushing changes to GitHub**: Once you're ready to share your changes with the team, you can push your commits to GitHub with `git push`.  
  
6. **Pulling changes from GitHub**: To get the latest changes that others have pushed to GitHub, you can use `git pull`.  
  
In conclusion, using Git for source control and GitHub for external hosting is a powerful combination that can greatly enhance your workflow and productivity. Both are industry standards and will be invaluable tools in your software development journey.  

## Introduction to Git  
  
[Git](https://git-scm.com/) is an open-source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. Created by Linus Torvalds in 2005, Git has since become the most widely adopted version control system by developers around the world.  
  
Here are some of the key features of Git:  
  
- **Distributed Version Control**: Unlike centralized version control systems, Git gives every developer a local copy of the entire development history, and changes are copied from one such repository to another. This allows you to work offline and not rely on a central server to store all the versions of a project’s files.  
  
- **Branching and Merging**: The Git feature that really makes it stand apart from nearly every other SCM out there is its branching model. Git allows and encourages you to have multiple local branches that can be entirely independent of each other. The creation, merging, and deletion of those lines of development takes seconds.  
  
    For example, if you're working on a new feature named `user-authentication`, you can create a new branch specifically for that feature (`git checkout -b user-authentication`). Once the feature is completed, you can merge it back to the main branch (`git merge user-authentication`).  
  
- **Speed**: Git is fast. With Git, nearly all operations are performed locally, giving it a huge speed advantage on centralized systems that have to constantly communicate with a server.  
  
- **Data Integrity**: Git uses a data model that ensures the cryptographic integrity of every bit of your project. Every file and commit is checksummed and retrieved by its checksum when checked back out. It’s impossible to get anything out of Git other than the exact bits you put in.  
  
- **Staging Area**: Unlike most SCMs, Git has something called a "staging area" or "index". This is an intermediate area where commits can be formatted and reviewed before completing the commit.  
  
    For instance, if you have changed two files (`file1.txt` and `file2.txt`), but you want to commit them separately, you can add one of them to the staging area (`git add file1.txt`) and commit it (`git commit -m "Your message here"`). Then repeat the process for the other file.  
  
- **Free and Open Source**: Git is released under a very permissive open source license, making it available for everyone to use.  
  
Git is not just a tool, it's an entire workflow that encourages developers to work together without stepping on each other's toes. It's widely used by individuals and organizations around the world to write software, track changes, and collaborate.  

### Git Commands Cheat Sheet  
  
- `git init`: Initializes a new Git repository.
- `git add`: Adds a file to the staging area. Usage: `git add filename.txt`
- `git commit`: Commits changes to the repository. Usage: `git commit -m "commit message"`  
- `git push`: Pushes changes to a remote repository. Usage: `git push origin main`  
- `git pull`: Fetches and merges changes from a remote repository. Usage: `git pull origin main`  
- `git branch`: Creates a new branch. Usage: `git branch feature_branch`  
- `git checkout`: Switches to a different branch. Usage: `git checkout feature_branch`  
- `git merge`: Merges changes from different branches. Usage: `git merge feature_branch`  
- `git branch -d`: Deletes a local branch. Usage: `git branch -d feature_branch`  
- `git push origin --delete`: Deletes a remote branch. Usage: `git push origin --delete feature_branch`  
- `git status`: Shows the status of changes as untracked, modified, or staged.  
- `git log`: Displays the history of commits.
- `git clone`: Clones a repository into a new directory. This command copies an existing Git repository, typically from a remote source like GitHub. Usage: `git clone https://github.com/username/repository.git`  

### Git Commands Flow with Examples

#### Cloning a Repository
To clone a repository from GitHub, use the `git clone` command followed by the repository's URL. For example, to clone a repository located at `https://github.com/username/repository.git`, you would use the following command:

```
git clone https://github.com/username/repository.git
```
This command creates a copy of the repository on your local machine in a new directory named after the repository.

#### Creating a Branch
After cloning the repository, navigate into the new directory with `cd repository`. Here repository is the name of your repository. Then create a branch using the `git branch` command followed by the name of the new branch. For example, to create a branch named `feature/new_feature`, you would use the following command:

```
git branch feature/new_feature
```
Then, to switch to your new branch, use the git checkout command:
```
git checkout feature/new_feature  
```

#### Adding Items to Commit, Then Commit with Comment
First, add the items you want to commit using the `git add` command. You can add all changes by using `.` or specify a file:
```
git add .  
```
or  
```
git add file_name  
```
Then, commit your changes with a comment using the `git commit` command:
```
git commit -m "Your comment here"  
```

#### Pull, Commit, Push
To pull the latest changes from the remote repository, use the `git pull` command:
```
git pull origin branch_name  
```
Then, `commit` your changes and `push` them to the remote repository:
```
git commit -m "Your comment here"  
git push origin branch_name  
```

#### Solving Merge Conflict
When you encounter a merge conflict, first open the file with the conflict. You'll see markers indicating the conflicted area:

```
<<<<<<< HEAD  
...your changes...  
=======  
...changes on the branch you're merging...  
>>>>>>> branch_name  
```

Edit the file to resolve the conflict, then add and `commit` the file:
```
git add file_name  
git commit -m "Resolved merge conflict"  
```

#### Removing a Branch
To remove a local branch, use the git branch -d command:
```
git branch -d branch_name  
```
To remove a remote branch, use the git push command with --delete:
```
git push origin --delete branch_name  
```
  
## Introduction to GitHub  
  
[GitHub](https://github.com) is a web-based hosting service for version control using Git. It is a platform where developers can collaborate on projects, making it easier for individuals and teams to work together seamlessly. It's been seamlessly integrated with Git, the open-source version control system. This means you can use GitHub to manage your Git repositories and take advantage of all the other features and functionalities that GitHub offers.  
  
Here are some of the key features of GitHub:  
  
- **Repositories**: A repository (or "repo") is like a project folder where all the project files (code, documentation, etc.) live. It also includes the history of every file change.  
  
- **Forks**: This is a copy of a repository that sits in your account rather than the account from which you forked the data from. It allows you to experiment with changes without affecting the original project.  
  
- **Pull Requests**: This feature allows developers to tell others about the changes they've pushed to a branch in a repository. Once a pull request is opened, you can discuss and review the potential changes with collaborators and add follow-up commits before your changes are merged into the base branch.  
  
- **Issue Tracking**: GitHub provides an issue tracking feature which allows you to track bugs, enhancements, or other requests.  
  
- **GitHub Pages**: This feature allows you to host a website directly from a GitHub repository.  
  
- **Marketplace**: Here you can find apps and actions to improve and extend your workflow. From continuous integration to project management and code review, this marketplace is a source of tools developed specifically for GitHub.  
  
- **Security**: GitHub provides advanced security features like code scanning and secret scanning to prevent security vulnerabilities.  
  
GitHub is not just a tool, but also a community. It's a platform where people can share ideas, collaborate on projects, and contribute to the open-source community. It's widely used by developers around the world and has become an essential part of the software development process.  

### Github Flow with Examples

#### Creating a Pull Request Between the Branch and Main
Pull requests are created on the GitHub website. Go to your repository on GitHub, select the branch that contains your changes, and click 'New pull request'. Select main as the base branch and your feature branch as the compare branch, then click 'Create pull request'.
  
## Introduction to Gitflow  
  
Gitflow is a branch management strategy built for Git, which was introduced by Vincent Driessen at nvie. It is a consistent way to manage and track features, releases, and hotfixes in your Git repositories.  
  
The Gitflow Workflow defines a strict branching model designed around the project release. This provides a robust framework for managing larger projects and can be used to deploy robust software release cycles.  
  
## Gitflow Branching Strategy Cheat Sheet  
  
Gitflow utilizes two main branches to record the history of the project:  
  
- `master` _or_ `main`: The main branch where the source code always reflects a production-ready state. This branch is used to release code to production.  
  
- `develop` _or_ `dev`: This is the branch where the source code always reflects a state with the latest delivered development changes for the next release. This is the main branch where developers work on a day-to-day basis.  
  
In addition to these main branches, Gitflow has support for different types of auxiliary branches:  
  
- `Feature`: These branches are used to develop new features for the upcoming or a distant future release. When starting development of a feature, the target release in which this feature will be incorporated may well be unknown at that point. The essence of a feature branch is that it exists as long as the feature is in development, but will eventually be merged back into develop or discarded. The branch naming can follow the pattern: `feature/<feature_name>`. For example, if you are working on a new login feature, the branch could be named `feature/new_login`.
  
- `Release`: Release branches support the preparation of a new production release. They allow for minor bug fixes and preparing meta-data for a release (version number, build dates, etc.). By doing all of this on a release branch, the develop branch is cleared to receive features for the next big release. The branch naming can follow the pattern: `release/<version>`. For example, if the upcoming release version is 1.2.0, the branch could be named `release/1.2.0`.  
  
- `Hotfix`: Hotfix branches are very much like release branches in that they are also meant to prepare for a new production release, albeit an unplanned one. They arise from the necessity to act immediately upon an undesired state of a live production version. When a critical bug in a production version must be resolved immediately, a hotfix branch may be branched off from the corresponding tag on the master branch that marks the production version. The branch naming can follow the pattern: `hotfix/<version>`. For example, if you are fixing a bug for version 1.2.1, the branch could be named `hotfix/1.2.1`.  

## Key Gitflow Terms  
  
Here are some key terms used in the Gitflow process:  
  
- `Feature`: A new feature being developed for the upcoming or a distant future release.  
- `Release`: This branch supports preparation of a new production release.  
- `Hotfix`: This branch is used to quickly patch production releases.  
- `Pull Request`: A mechanism for a developer to notify team members that they have completed a feature. This is a signal to initiate the code review process and eventually merge the changes into the develop or master branch.  
- `Merge`: A way to bring a forked branch back into the main code. 