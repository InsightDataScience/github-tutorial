# exercise 2

# Purpose
In several cases you will encounter files that don't belong in the repository. Typical examples include:
* credentials (passwords, usernames, keys)
* cached filed (.pyc)

Git allows users to add a .gitignore file to their top level directory to ignore these specific files

# Tasks
1. create a file in your repository called `my_super_secret_stuff.txt`
2. run a `git status` and see that `my_super_secret_stuff.txt` is untracked but can be added
3. create a `.gitignore` file if it does not already exist in your top level directory
4. at the top, add `my_super_secret_stuff.txt` to the file and save it
5. run a `git status` and see that `my_super_secret_stuff.txt` doesn't show up anymore!
6. `git add` your changes
7. `git commit` with a useful message
8. `git push` to the remote repository

