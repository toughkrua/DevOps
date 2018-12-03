Step one:	Configure ansible from zero to testing on localhost machine.

St1.1 	Create the ansible.conf and add vars `host_key_checking = False` for ingnore changes RSA fingerprint on remote hosts.

St2.2 	Create the hosts file and configure this for two variants connection to the localhost machine like any other remote hosts

    For now, Command:
    `ansible all -m file -a "path=/home/file state=touch mode=555" -b --extra-vars="ansible_become_pass=<password>"`
        will do create file on both hosts
    `ansible all -m file -a "path=/home/file state=touch mode=555" -b`
        will do create file on machine1 only

NOTE:	For avoid manual refer the sudo password to execute a sudo command on remote host, you need point the pass in ansible config files, or enable passless sudo on remote	host - in sudoers file: `%user    ALL=(ALL) NOPASSWD:ALL`
	

Step two:	Create local Git repository for DevOps project.	Create account, project DevOps with README.md on GitHub. Merge local and remote project and push commit.

St2.1	On dir DevOps do `git init .`
St2.2	Create account https://github.com/toughkrua on https://github.com and https://github.com/toughkrua/DevOps
St2.3.1	Make some changes on file README.md through web https://github.com and do commite
St2.3.2	Clone DevOps project: `git clone https://github.com/toughkrua/DevOps` `cd DevOps`
St2.3.3	For delete from github first unnecessary snapshot and leave only last one that is needed: `rm -rf .git` `git init .` git push https://github.com/toughkrua/DevOps --force` `cd ..` `remove -rf DevOps`
St2.3.4 Merge project and push it on remote repo `git pull origin master --allow-unrelated-histories` redo README.md `git add README.md` `git commit` `git push --set-upstream origin master` 
