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

git push 
- pushes file to repository

git clone https://github.com/ikrs/ProGit.git
- get a copy of a repository

git status
- main tool to determine which files are in which state

git status -s
- see your changes in a more compact way 

git config credential.helper 'cache --timeout=1800'
- on push to repository Git wont ask you for your username and password for 30 min



