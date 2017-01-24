# github-tutorial

# Git and GitHub

### What?
- **Git:** a version control system that keeps track of code changes
- **GitHub:** a popular server for hosting repositories

### Why?
- Keeps a full history of changes
- Allows multiple programmers to work on the same codebase
- Is efficient and lightweight (records file changes, not file contents)
- Public repositories on GitHub can serve as a coding resume.

### How?
- That's what this session is for!

# Git and GitHub Setup

### 1. Create a GitHub account

Create a Github account through the Github website.

- Go to https://github.com/ and follow on-screen instructions to create a user account

- Tip: Choose a job-appropriate user name if possible

<!--![git-homepage](img/git-homepage.png)-->

### 2. Install Git

Install Git on your computer (through Terminal for Mac or Ubuntu).

- Installing on Mac: `$ brew install git`  
- Installing on Ubuntu: `$ apt-get install git`  
- Installing on Windows: [http://git-scm.com/downloads](http://git-scm.com/downloads)

- Tip: If you are running into trouble, try [here](http://git-scm.com/book/en/Getting-Started-Installing-Git)
- Tip: To check if git is already installed, try `$ git` in Terminal

![git-cli](img/git-cli.png)

### 3. Configure Git

Configure Git so that Github can recognize your commits (in Terminal).

- Run the following commands in Terminal to configure git:

	`$ git config --global user.name "[insert your user name here]"`  
	`$ git config --global user.email "[insert your email here]"`

- Tip: The gloabl config settings can be accessed and manually edited in `~/.gitconfig`

### 4. Fork the tutorial repository to your account

Fork the tutorial repository to your account through the Github webpage.

- On the [GitHub repo page](https://github.com/InsightDataScience/github-tutorial), in the top right corner of the page under the photo of your account, click the Fork button (see below for example).
- Select your account when prompted. This should fork the github-tutorial repository to your account.

Tip: If you successfully forked the tutorial repository, you should see the name of the repository as [your user name]/github-tutorial

![git-fork](img/git-fork.png)

### 5. Clone the repository to your local machine

Clone this repository (the remote repository) to your local machine.

- On your tutorial repository webpage, click the green "Clone or download" button on the right side of the page.
- Select the "Use HTTPS" option if it is available.
- Copy the link.

- In Terminal, navigate to your development folder.

	`$ cd [path to your development folder]`

- Type `git clone` into Terminal, followed by the repository link you copied (see below for example)
	  
	`$ git clone [link to your forked tutorial repository]`

<!--![git-clone](img/git-clone.png)-->

### You are now ready to use version control with Git and Github!

# Git Concepts and Vocabulary

### Change (aka Diff)

Git maintains version control by tracking the changes or diffs between file versions. 

You can change a file by doing one of two things:
1. File creation, renaming, or deletion.  
2. Insertion or deletion of a line in a file (a modified line is both an insertion and a deletion)

Git represents insertions or added changes with a `+` and deletions or removed changes with a `-`

![git-hello-diff](img/git-hello-diff.png)

Tip: You can use the command `git diff` to see how a file has changed since its last commit or between two branches.

### Commit

Commits are a series of changes that records incremental updates to a series of files.

Each commit a global unique hash (calculated from contents of file) that serves as an identifier.

![git-commit](img/git-commit.png)

### Branch

A branch refers to a linear series of commits.

A codebase can be calculated by applying changes to files in each commit in succession.

![git-commit-history](img/git-commit-history.png)

### Repository

A repository refers to a tree structure that contains many branches. Each branch represents a different state of the code. 

Branches can be formed at any commit, and two branches can be merged together by summing their changes (assuming there are no conflicts).

# Basic Git Tutorial

## Basic Workflow

There are three basic commands that part of the typical workflow when doing version control with git. These commands are **add, commit and push**.

### 0. Create a file

First, create an example file to track using Git.

- In Terminal, navigate to your repository folder.
- Create a Python file called `hello.py` using your favorite editor
- Write some (very simple) code.

	```def salutations(name):  
	print "Hello " + name'
	```

### git add

After making a change to your code, add the file to git to track the change.


- In a Terminal, navigate to your repository and create a python file called `hello.py` using your favorite editor (e.g., `nano hello.py`, `vim hello.py`, `subl hello.py`)
- Write some (very simple) code
- Add the file to be tracked by git:  
`$ git add hello.py` 

 ![git-hello-1](img/git-hello-1.png)

### Commit the Tracked File
- Commit the added file to the git repo and add a message describing the change:  
`$ git commit -m "Initial commit"`  

### Push Updates to a Repository
- Use `git push origin master` to push local commits to the remote branch:  
`$ git push origin master`

### Useful Calls
**git status**
- To check the status of your repo (which branch you're on, which files are untracked, which files are modified, which files are added/tracked), use `git status`  
`$ git status`

**git diff**
- To see how your file has changed before you add/commit the file, use `git diff`  
`$ git diff hello.py`

## Additional Info

### Ignore Files in the Repository
- Sometimes there are sensitive files you do not want tracked to Github (e.g., passwords)
- In your repository, add file names to the `.gitignore` file to prevent them from being revision controlled.
- Make a file called `credentials.json` in your directory
- Open (or create) the file `.gitignore` and add `credentials.json` to the file. Save and close.
- Add, commit, and push your changes to the `.gitignore` file:  
`$ git add .gitignore`  
`$ git commit -m "Modifying .gitignore"`  
`$ git push origin master`

### Create a GitHub Repo
On GitHub create a new repository named `git-demo` by clicking on Respositories, then New from your home page.

![git-profile](img/git-profile.png)

Initialize with a Readme and add a .gitignore

![git-repo-create](img/git-repo-create.png)

Now your repo is created! From the home page of your repo, copy the repo URL. 

![git-new-repo-clone](img/git-new-repo-clone.png)

Clone the repo to your development folder on your local machine.  
`$ git clone https://github.com/jillinsight/git-demo.git`

### Developing on a new branch
*Create a new branch locally*
- To create a new branch, use the following command. Replace `add-excitement` with the name of your new branch  
`$ git checkout -b add-excitement`

*Push the new branch to remote*  
- Push the new branch to remote  
`$ git push origin add-excitement`

*Commit to a new branch*
- Make a change to `hello.py` by adding exclamation points after "Hello World"
- After making this change, push your changes to the new branch  
`$ git add hello.py`  
`$ git commit -m "Add excitement to hello world"`  
`$ git push origin add-excitement`

![git-hello-2](img/git-hello-2.png)

*Merge a new branch*
- Checkout the branch you want to merge into (preferably the branch you created the new branch off of)
- Merge the changed branch into that branch  
`$ git checkout master`  
`$ git merge add-excitement`

*Delete the new branch*
- If you are done developing on the new branch, delete the branch locally and remotely  
`$ git branch -d add-excitement # local delete`  
`$ git push origin --delete add-excitement # remote delete`

*Git Branch*
- To see which branch you're on, use `git branch` or `git status`

### Pull Requests

*Create a pull request*
- When developing on a team, you rarely merge branches locally. You will typically merge branches via pull requests.
- On the GitHub repo, click on Pull requests from the options.
- Click the New pull request button
- From the dropdown menu, select the branch you want to serve as your base (the branch you will merge into). Select the branch you want to merge from the compare dropdown.
- Click Create pull request.
- Assign someone to review your code and click Create pull request

*Accept a pull request*
- If you are reviewing a pull request, check out the Commits and Files changed to view diffs between the base branch and compare branch.
- If you are happy with the changes (and there are no conflicts), click Merge pull request and Confirm request. (Don't forget to add a comment telling your co-developer what an awesome job they did!)
- Delete the branch if it is no longer needed (remotely)

*Pull changes to local*
- Don't forget to pull the changed branch back down to your local machine after a pull request is made. Replace master with the branch you merged into.  
`$ git pull origin master`

*Delete the local branch*
- If you deleted the remote branch, delete the local branch

## Best Practices

### When should I commit?
Ideally you commit “working” code, so that you can return to a working state if necessary. Also, each commit should have one logical task that can be summarized in one phrase.

### When should I push?
Always right after you commit. Why wouldn’t you want to have an immediate back up?

### Do I have to have commit messages?
You at least need a descriptive title. This is an important part of code documentation (especially in a multi-developer environment).

*Thank you to Mike Grinolds for his slides and GitHub tutorial!*
