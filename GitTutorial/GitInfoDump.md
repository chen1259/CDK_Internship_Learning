# Heres some basic terms and commands used for Git

### Commands

git init : initialize a git repository

git status : check the current state of the project

git add filename : Start tracking changes made to the filename or add it to the staging area

git add -A . : The dot at the end means current directory so everything beneath and in it 
is added.  -A ensures even file deletions are included.

git reset filename :  Remove a file or files from the staging area 

git commit -m "Message here" :  To store staged changes in the repository we use commit 
and -m and then a message after on what we changed

git add '*.txt' : A wildcard way to store stuff that will add many files of the same type.
This one in particular will add a bunch of .txt files into your directory.

git log :  Git's way to journal all the changes committed in the order you committed them

git remote add origin httpsURL :  Takes a remote name (origin) and a repository URL (httpsURL)
in order to add a remote repository

git push -u origin master : Tells Git where to put our commits and when we're ready.  This pushes our 
local changes to our origin repo on GitHub.  The name of the remote in this case is also origin and 
default local branch name is master.  The -u is for remembering parameters for future setup.

git pull origin master : Check for changes on the GitHub repo and pull down any new changes

git diff HEAD :  Takes a look at whats different from the last commit, HEAD is for the most recent commit
If instead of HEAD you type in a file name then we can look at changes within the file.

git diff --staged : This allows you to see the changes that were staged

git reset filename : Unstage files

git checkout -- <target> :  Files can be changed back to how they were at the last commit with this command.
Get rid of all the changes since the last commit

git branch branch_name : Creates a copy (aka branch) of their code to make seperate commits to.  Can merge 
it back to their main branch later.  

git branch :  See all the local branches.  

git checkout branch_name : Switch branches

git checkout -b branch_name :  To checkout and create a branch at the same time, same as 
git branch branch_name and git checkout branch_name combined

git rm '*.txt' : Remove all the actual files from disk as well as stage removal of the files for us.  This one
uses a wildcard again.

git merge branch_name :  Merges changes from the branch into the master branch

git branch -d branch_name : Deletes a branch one you merge it with master

git push : Push everything you've been working on into your remote repo.

___
 
### Terms

Directory:
A folder used for storing multiple files.

Repository:
A directory where Git has been initialized to start version controlling your files.

staged:
Files are ready to be committed.
unstaged:
Files with changes that have not been prepared to be committed.

untracked:
Files aren't tracked by Git yet. This usually indicates a newly created file.

deleted:
File has been deleted and is waiting to be removed from Git.

Staging Area:
A place where we can group files together before we "commit" them to Git.

Commit
A "commit" is a snapshot of our repository. This way if we ever need to look back at 
the changes we've made (or if someone else does), we will see a nice timeline of all changes.

Wildcards:
We need quotes so that Git will receive the wildcard before our shell can interfere with 
it. Without quotes our shell will only execute the wildcard search within the current 
directory. Git will receive the list of files the shell found instead of the wildcard 
and it will not be able to add the files inside of the octofamily directory.

HEAD
The HEAD is a pointer that holds your position within all your different commits. 
By default HEAD points to your most recent commit, so it can be used as a quick way 
to reference that commit without having to look up the SHA.

Branching
Branches are what naturally happens when you want to work on multiple features at the same time.
 You wouldn't want to end up with a master branch which has Feature A half done and Feature B half done.
Rather you'd separate the code base into two "snapshots" (branches) and work on and commit to 
them separately. As soon as one was ready, you might merge this branch back into the master branch 
and push it to the remote server.

___

### Advice

Check all the things!
When using wildcards you want to be extra careful when doing commits. Make sure to check
what files and folders are staged by using git status before you do the actual commit.
This way you can be sure you're committing only the things you want.

More useful logs:
Use git log --summary to see more information for each commit. You can see where new files were 
added for the first time or where files were deleted. It's a good overview of what's going on in the project.

git remote:
Git doesn't care what you name your remotes, but it's typical to name your main one origin.
It's also a good idea for your main repository to be on a remote server like GitHub
in case your machine is lost at sea during a transatlantic boat cruise or crushed by 

three monkey statues during an earthquake.

Cool Stuff:
When you start to get the hang of git you can do some really cool things with hooks when you push.
For example, you can upload directly to a webserver whenever you push to your master remote 
instead of having to upload your site with an ftp client. Check out Customizing Git - Git Hooks for more information.

git stash:
Sometimes when you go to pull you may have changes you don't want to commit just yet. One option 
you have, other than commiting, is to stash the changes.
Use the command 'git stash' to stash your changes, and 'git stash apply' to re-apply your changes
 after your pull.

Commit Etiquette:
You want to try to keep related changes together in separate commits. Using 'git diff' gives 
you a good overview of changes you have made and lets you add files or directories one at a 
time and commit them separately.

So you may be wondering, why do I have to use this '--' thing? git checkout seems to work 
fine without it. It's simply promising the command line that there are no more options after 
the '--'. This way if you happen to have a branch named octocat.txt, it will still revert the 
file, instead of switching to the branch of the same name.

Remove all the things!
Removing one file is great and all, but what if you want to remove an entire folder? 
You can use the recursive option on git rm: git rm -r folder_of_cats
This will recursively remove all folders and files from the given directory.

The '-a' option
If you happen to delete a file without using 'git rm' you'll find that you still have to 'git rm' 
the deleted files from the working tree. You can save this step by using the '-a' option on 'git 
commit', which auto removes deleted files with the commit.
git commit -am "Delete stuff"

Pull Requests
If you're hosting your repo on GitHub, you can do something called a pull request.
A pull request allows the boss of the project to look through your changes and make comments 
before deciding to merge in the change. It's a really great feature that is used all the 
time for remote workers and open-source projects.
Check out the pull request help page for more information.

Merge Conflicts
Merge Conflicts can occur when changes are made to a file at the same time. A lot of people get 
really scared when a conflict happens, but fear not! They aren't that scary, you just need to decide which code to keep.
Merge conflicts are beyond the scope of this course, but if you're interested in reading more, 
take a look the section of the Pro Git book on how conflicts are presented.

Force delete
What if you have been working on a feature branch and you decide you really don't want this 
feature anymore? You might decide to delete the branch since you're scrapping the idea. 
You'll notice that git branch -d bad_feature doesn't work. This is because -d won't let 
you delete something that hasn't been merged.
You can either add the --force (-f) option or use -D which combines -d -f together into one command.

Learning more about Git
We only scratched the surface of Git in this course. There is so much more you can do with it. 
Check out the Git documentation for a full list of functions.
The Pro Git book, by Scott Chacon, is an excellent resource to teach you the inner workings of Git.
help.github and GitHub Training are also great for anything related to Git in general and using Git with GitHub.
