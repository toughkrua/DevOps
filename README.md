### Step one:	Configure ansible from zero to testing on localhost machine.

1.1 	Create the ansible.conf and add vars `host_key_checking = False` for ingnore changes
	RSA fingerprint on remote hosts.
2.2 	Create the hosts file and configure this for two variants connection to the
	localhost machine like any other remote hosts

  For now, comand:
    `ansible all -m file -a "path=/home/file state=touch mode=555" -b --extra-vars="ansible_become_pass=<password>"`
   will do create file on both hosts  
    `ansible all -m file -a "path=/home/file state=touch mode=555" -b`
   will do create file on machine1 only

NOTE:	For avoid manual refer the sudo password to execute a sudo command on remote host,
        you need point the pass in ansible config files, or enable passless sudo on remote
        host - in sudoers file: `%user    ALL=(ALL) NOPASSWD:ALL`
	
### Step two:   Create local Git repository for DevOps project.	Create account, project
###             DevOps with README.md on GitHub. Merge local and remote project and push commit.

2.1	On dir DevOps do `git init .`  
2.2	Create account <https://github.com/toughkrua> on <https://github.com> and [DevOps project](https://github.com/toughkrua/DevOps "The my personal DevOps training experience")  
2.3.1	Make some changes on file README.md through web https://github.com and do push commit  
2.3.2	Clone DevOps project: `git clone https://github.com/toughkrua/DevOps` `cd DevOps`  
2.3.3	For delete from github first unnecessary snapshot and leave only last one that is needed:  
	`rm -rf .git` `git init .` `git push https://github.com/toughkrua/DevOps --force` `cd ..`  
	`remove -rf DevOps`  
2.3.4	Merge project and push it on remote repo `git pull origin master --allow-unrelated-histories`  
        redo README.md `git add README.md` `git commit` `git push --set-upstream origin master`

### Step three:	Create branch "markdown" and formating README.md file to markdown syntax.
###		Connect to GitHub with SSH key. Push "markdown" branch.
###		Merge "markdown" with "master" branch.
###		Edit README.md on "markdown" branch, amend last "markdown" commit on local and remote repository.
###	 	Merge "markdown" and "master" again, amend last "master" commit on local and remote repository.
3.1.1	`git checkout -b markdown` or `git branch markdown` `git checkout markdown`  
3.1.2	Formatting README.md with markdown syntax and do commit `git add README.md`
	`git commit -m "Formatting README.md with markdown syntax"` or
	git commit -a -m "Formatting README.md with markdown syntax"
3.2	Add public SSH RSA key to GitHub by web. Change project url  
	`git remote set-url origin git@github.com:toughkrua/DevOps.git`  
3.2.2	`git push --set-upstream origin master` 
3.3	`git checkout master` `git merge markdown` `git push`  
3.4	`git checkout markdown`, edit README.md, `git commit -a --amend` `git push --force`  
3.5	`git checkout master` `git reset --hard HEAD~1` `git merge markdown` `git push --force`	
