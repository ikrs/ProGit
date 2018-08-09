# ProGit
Learning Pro Git

		FIRST-TIME GIT SETUP

`git config --list`	
- list all the Git settings 

`git help config`
- shows comprehensive manual page for give command


		GIT BASICS


`git init`
- creates new subdirectory named .git and inside it creates Git repository skeleton, nothing in project is tracked yet

`git add README.md`
- command that specifies the file you want to track

`git commit`
- commits the file to be pushed

`git commit -m 'Init commit'`
- adds message to your commit 

`git push` 
- pushes file to repository

`git clone https://github.com/ikrs/ProGit.git`
- get a copy of a repository

`git status`
- main tool to determine which files are in which state

`git status -s`
- see your changes in a more compact way 

`git config credential.helper 'cache --timeout=1800'`
- on push to repository Git wont ask you for your username and password for 30 min after the next push


`.gitignore`
- *.[oa] -> ignore any file ending in ".o" or ".a"
- *~ -> ignore all files whose names end with a tilde, which is used by many text editors to mark temp files

		Example .gitignore file
		#ignore all .a files
		*.a

		#but do track lib.a, even though you're ignoring .a files above 
		!lib.a 

		#only ignore the TODO file in the current directory,not subdir/TODO
		/TODO

		#ignore all files in the build/ directory
		build/

		#ignore doc/notes.txt, but not doc/server/arch.txt
		doc/*.txt

		#ignore all.pdf files in the doc/ directory any any of its subdirectories
		doc/**/*.pdf


GitHub maintains a fairly comprehensive list of good .gitignore file examples for dozens of projects and languages at 
https://github.com/github/gitignore if you want a starting point for your project.


`git diff`
- shows you the exact lines added and removed, while git status shows only file names witch contain changes
- only shows changes that are unstaged (didnt run git add)

`git diff --staged`
- Used to see what you've staged (git add) that will go into your next commit

`git commit -a`
- makes git automatically stage (add) every file that is already tracked, letting you skip the git add part

`git rm filename`
- remove file from Git and from staging area, it also deleats it locally

`git rm -f filename`
- if you modified the file and added it to staging area you must force remove it, it also deleats it locally

`git rm --cached filename`
- keep the file in your working three but remove it from staging area, preatty usefull if we forgot to add some file in .gitignore

`git mv file_from file_to`
- rename a file in Git

`git log`
- view the commit history in current repository in reverse chronological order
- look online for more git log options

`git log -p`
- shows difference introduced in each commit (something like git diff)

`git log -p -2` 
- shows difference in last 2 commits

`git log --stat`
- abbreviated stats for each commit (how many files were changed, how many lines in those files changed), it also puts a summary of the information at the end

`git log --since=2.weeks`
- this command gets the list of commits made in last two weeks
- it works with alot of formats like "2018-01-15", "2 years 1 day 1 minute ago", ...

`git log --author=ikrs`
- show commits of a specific author

`git log --grep=test`
- search for keyword "test" in commit messages

`git log --pretty=format/oneline/short/full/fuller`
- changes the log output to formats other than the default
- "format" option allows you to specify your own log output format, list of all format options can be found online
 		
		Example of custom format

		git log -4 --pretty=format:"%h - %an, %ar : %s" 
		306394b - ikrs, 13 minutes ago : git mv and git log
		82a5733 - ikrs, 18 minutes ago : git rm and related actions
		8677eec - ikrs, 32 minutes ago : git commit -a
		1973597 - ikrs, 3 hours ago : git diff --staged (add)

- the "oneline" and "format" are particulary useful with another log option called --graph, this option adds a nice little ASCII graph showing your branch and merge history

		Example of a --graph option

		git log --pretty=format:"%h %s" --graph
		* 2d3acf9 ignore errors from SIGCHLD on trap
		* 5e3ee11 Merge branch 'master' of git://github.com/dustin/grit
		|\
		| * 420eac9 Added a method for getting the current branch.
		* | 30e367c timeout code and tests
		* | 5a09431 add timeout protection to grit
		* | e1193f8 support for heads with slashes in them
		|/
		* d6016bc require time for xmlschema
		* 11d191e Merge branch 'defunkt' into local


`git log -S function_name`
- colloquially reffered to as Git's "pickaxe" option
- takes a string and shows only those commits that changed the number of occurances of that string

`git log --author=ikrs --no-merges`
- prevent the display of merge commits cluttering up your log history

`git commit --amend`
- if you want to redo the commit, make the additional changes you forgot, stage them and commit again using --amend option so you end up with a single commit

		$ git commit -m 'initial commit'
		$ git add forgotten_file
		$ git commit --amend


`git reset HEAD <fileName>`
- when you staged ( add ) file you didnt want to stage you can remove it from staging area

`git checkout --<fileName>`
- dont want to keep the changes to the file, you can revert it back to what it looked like when you last commited

`git remote` 
-see which remote servers you have configured

`git remote -v`
- shows you the URL that Git has stored for the shortname to be used when reading and writing to that remote

`git fetch remote`
- get data from your remote projects
- this commands goes out to that remote project and pulls down all the data from that remote project that you dont have yet

`git remote add <shortname> <url>`
- add a new remote repository explicitly
		git remote add paul https://github.com/paulboone/ticgit
- now you can use the string paul in the command line instead of the whole URL, if we want to fetch all the information that Paul has but that you dont yet have in your repository you can run
		git fetch paul
- paul master branch is now accessible locally as 'pb/master', you can merge it into one of your branches or you can check out a local branch at that point if you want to inspect it

`git pull`
- automatically fetch and then merge that remote branch into your current branch. This may be an easier or more comfortable workflow

`git push <remote> <branch>`
- if you want to push your master branch to origin server then you can run
		git push origin master
- this works only if you cloned from a server to which you have write access and if nobody has pushed in the meantime

`git remote show <remote>`
- shows more information about a particular remote
		git remote show origin
