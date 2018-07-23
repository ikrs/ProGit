# ProGit
Learning Pro Git

		FIRST-TIME GIT SETUP

git config --list	
- list all the Git settings 

git help config
- shows comprehensive manual page for give command


		GIT BASICS


git init
- creates new subdirectory named .git and inside it creates Git repository skeleton, nothing in project is tracked yet

git add README.md
- command that specifies the file you want to track

git commit
- commits the file to be pushed

git commit -m 'Init commit'
- adds message to your commit 

git push 
- pushes file to repository

git clone https://github.com/ikrs/ProGit.git
- get a copy of a repository

git status
- main tool to determine which files are in which state

git status -s
- see your changes in a more compact way 

git config credential.helper 'cache --timeout=1800'
- on push to repository Git wont ask you for your username and password for 30 min after the next push


.gitignore
- *.[oa] -> ignore any file ending in ".o" or ".a"
- +~ -> ignore all files whose names end with a tilde, which is used by many text editors to mark temp files


ignore all .a files
*.a

but do track lib.a, even though you're ignoring .a files above
!lib.a

only ignore the TODO file in the current directory, not subdir/TODO
/TODO

ignore all files in the build/ directory
build/

ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

ignore all.pdf files in the doc/ directory any any of its subdirectories
doc/**/*.pdf


GitHub maintains a fairly comprehensive list of good .gitignore file examples for dozens of projects and languages at 
https://github.com/github/gitignore if you want a starting point for your project.



