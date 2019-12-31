# Useful Spells

## Linux

### File system & disk operations

* ls -t -> 	list files sorts last modified newest on top
* ls -tr -> same as above reversed

* find . -type f -exec dos2unix {} \; --> convert line endings in the whole directory tree

* sudo ln -s /opt/maven/bin/mvn /usr/bin/mvn
* sudo ln -s /usr/share/groovy/groovy-2.5.7/bin/groovy /usr/bin/groovy

* du -sh /etc/  --> report only the total disk space occupied by a directory tree and to suppress subdirectories
* du -sh ./*/ --> list out total memory for each subfolder in current path
* du -a -h /etc/ --> same as above + including files not only dirs
* du -ch *.png --> see the size of each png file in the current directory
* du -a /etc/ | sort -n -r | head -n 10  --> List top 10 directories eating disk space in /etc/

* df -h  --> report file system disk space usage in human form
* df -h --total  --> option to have the total

## SSH connection & file operations

* ssh-add -c mykeypair.pem --> Linux add private key to the authentication agent
* ssh-add -K mykeypair.pem --> MacOS same as above
* ssh -A <user>@<host> --> ssh to host machine, then connect to any host that has same private key for authentication

* ssh -i ~/.ssh/id_rsa.pub USER@SERVER
* scp -i ~/.ssh/id_rsa.pub FILENAME USER@SERVER:/home/USER/FILENAME

### Administration commands

* sudo -l --> lists all privileges from /etc/sudoers for a user
* sudo -s --> inherits your current user environment
* sudo -i --> gives clean environment, like you get just after login
* sudo update-alternatives --config editor -> changes visudo editor
* sudo visudo  -> launches the /etc/sudoers file in an editor
* sudo visudo -f /etc/sudoers.d/file_to_edit  -> launches any other sudoers file in visudo

* [SUID](http://www.linuxnix.com/suid-set-suid-linuxunix/)

### Linux LIMITS checking and changing of them

* cat /proc/sys/kernel/pid_max  --> shows maximum number of processes particular kernel can run
* cat /proc/PID/limits  --> shows limits of a particular process

* ulimit -a  --> shows limits for a user that executes it
* ulimit -Hu --> shows hard limits for max user processes (-u)
* ulimit -Su --> shows soft limits for max user processes (-u) you can add any letter from -a list for this to check the limit

* /etc/security/limits.conf  --> This file enforces limits on users/groups etc.
* /etc/security/limit.d/ --> Files in this directory overrides any settings done in limits.conf file. Files here
                           are being read in the alphabetical order and that is how settings are also being overridden.

### Linux services

* service --status-all  --> lists all services on linux

* chkconfig --add myscript  --> adds a service to run level
* chkconfig --level 2345 myscript on --> enable it for particular run level
* chkconfig --level 2345 myscript off --> removes from run level
* chkconfig --del myscript --> removes service from chkconfig
* chkconfig --list | grep myscript  --> linsts chkconfig service

### User / Group commands 

* cut -d: -f1 /etc/passwd --> lists all users
* useradd ĖM Ėg linuxuser Ėd /opt/linuxuser  linuxuser --> creates linuxuser user with /opt/linuxuser as home

* userdel USERANME --> removes user from the sytem
* usermod ĖaG wheel linuxuser --> add user linuxuser to wheel group
* gpasswd -a user group --> adds user to a group
* gpasswd -d user group --> removes user froma group

* groupadd linuxuser --> adds linuxuser group

* sudo chgrp -R tomcat /opt/tomcat --> Give the tomcat group ownership over the entire installation directory:
* sudo chmod -R g+r conf  --> give the tomcat group read access to the conf directory and all of its contents
* sudo chmod g+x conf  --> give the tomcat group execute access to the conf directory

* sudo chown -R tomcat webapps/ work/ temp/ logs/ --> make the tomcat user the owner of the webapps, work, temp, and logs directories:

* groups --> lists all current user's groups
* cut -d: -f1 /etc/group  --> Lists all the groups in the system
* groupdel GROUPNAME  --> deletes group from system

### Finding all files containing a text string on Linux

* grep -rnw 'directory' -e "pattern" -> -r or -R is recursive, -n is line number and -w stands match the whole word. -l (letter L) can be added to have just the file name.								 
* grep --include=\*.{c,h} -rnw 'directory' -e "pattern" -> Along with these, --exclude or --include parameter could be used for efficient searching.
* grep --exclude=\*.o -rnw 'directory' -e "pattern" -> Above will exclude searching all the files ending with .o extension.
* grep --exclude-dir={dir1,dir2,*.dst} -rnw 'directory' -e "pattern" -> Just like exclude file it's possible to exclude/include directories through --exclude-dir 
                                                                        and --include-dir parameter, the following shows how to integrate --exclude-dir
* grep -rl . -e "pattern" -> gives only the file names where pattern is located.																	  

### Find all unique extensions of files in root and subfolders exclude .git directory
* find . -type f -path '\*/.git\*' -prune -o -print | sed -rn 's|.\*/\[^/\]+\.(\[^/.\]+)$|\1|p' | sort -u 
*  Same as above with multiple directories
* find . -type d \(-path '\*/.git*' -o -path '\*/.idea*' \) -prune -o -print | sed -rn 's|.\*/\[^/\]+\.(\[^/.\]+)$|\1|p' | sort -u

### Untar \ Unzip  compressed stuff

* zip -r -s MaximumSize ArchiveName.zip FolderName/
* tar xvzf maven.tar.gz -C /var/jenkins_home/apache-maven/ -> untar to specified location
* unzip /usr/share/zip_file.zip -d /home/linuxuser/tmp/build/

### Checking TLS connections to server

* openssl s_client -connect domain.dupa.net:636 -tls1_2  --> checks server for TLS1.2 connection
* openssl s_client -connect domain.dupa.net:636 -showcerts

* nmap --script ssl-enum-ciphers -p 636 domain.dupa.net  --> Lists all possible TLS connections and ciphers

## Docker

* docker build -t username/repository . 
* docker build -t username/repository:latest -t username/repository:1.00-0 . --> builds image and tags with latest and specific version

### Run containers

* docker ps -> running containers
* docker ps -a -> all containers


* docker exec -it --user root username/repository:latest /bin/bash
* docker exec -it username/repository:latest /bin/sh
* docker run -it --rm -p 8080:8080 --name <container_name> username/repository:latest /bin/bash

### Containers Images management

* docker pull microsoft/mssql-server-linux -> updates image

* docker rm container_name -> removes docker container
* docker rmi image_name -> removes docker image from local repository

### Docker Volumes / Files

* docker volume ls -> lists volumes

* docker cp file.txt <container_name>:/directory/file.txt -> copies files from host to container
* docker cp <container_name>:/directory/file.txt x:\directory\file.txt-> copies files from container to host

### Docker network

* route | awk '/^default/ { print $2 }'  --> execute from within running container to get HOST IP address

### Inspect / monitor / troubleshoot containers

* docker inspect container_name -> shows container data

* docker events -> show what is happening in the container and <container id>
* docker logs <container id> -> shows logs from failed container

### Docker for Windows:

1. Check that you have the proper credentials setup under Credentials Manager->Windows Credentials->Dockerhost Filesystem Access
https://forums.docker.com/t/volume-mounts-in-windows-does-not-work/10693/45

## Git

### Repository Operations
* git remote -v --> view existing remotes
* git remote rename origin old_origin --> Change remote name from 'origin' to 'old_origin'
* git remote set-url origin git@server:group/project/project.git
* git remote set-url origin https://server:group/project/project.git
* git remote add origin git@server:group/project/project.git
* git remote remove origin

### Basic operations

* git checkout <branch_name> --> checks out branch
* git push --> pushes current branch into remote repository

* git branch -D <feature_branch> --> deletes local <feature_branch>
* git push origin :feature_branch --> pushes "an empty branch" into origin/feature_branch thus deleting remote branch



### Merge/Rebase
* git merge-base <feature_branch> <master> --> find <commit_id> of original base (<master>) for current <feature_branch>
* git rebase -i <commit_id> --> this will start rebasing from the base on which feature_branch was created
* git rebase -i HEAD~3 --> if you just want to clean up few latest commits this is useful. Will do rebase from the point where 3rd last commit occurred
* git rebase -i master --> rebasing current branch onto master branch

* git merge --no-ff <feature_branch> --> merges <feature_branch> into current branch with no fast-forward (with merge commit)


### Blogs, adivces
* [How to mirror a git repo to a new remote](https://makandracards.com/makandra/48818-how-to-mirror-a-git-repo-to-a-new-remote)
* [Gitkurwa - Jakub Nabrdalik](https://github.com/jakubnabrdalik/gitkurwa)

## Maven

* mvn help:effective-pom    --> shows what pom has and what was inherited from parent pom

### Dependencies related stuff

* mvn -o dependency:list -DincludeScope=compile -DoutputFile=dependencies.txt -DexcludeTransitive=true  --> list of dependencies
* mvn -o dependency:tree -DoutputType=text -DoutputFile=text.txt -Dverbose  --> List of dependeny trees
* mvn install:install-file -Dfile="X:\some_file-1.0.0.jar" -DgroupId="com.example" 
-DartifactId=some-artifact -Dversion="1.0.0" -Dpackaging=jar  --> Install 3rd Party dependency to local maven repo

### Maven Release Plugin

* mvn -P arekTest release:clean   --> clean the release stuff
* mvn -P arekTest release:rollback  --> rollbacks all the changes
* mvn clean release:prepare release:perform -P arekTest -DdevelopmentVersion=1.0.0-SNAPSHOT -DreleaseVersion=1.0.0.Release 
-DskipTests=true -DdryRun=false -DignoreSnapshots=true -DscmCommentPrefix="Some Comment"

### Maven Deploy using deploy-plugin

* mvn clean install
* mvn -P release deploy -DskipTests -Dmaven.install.skip=true

### Maven update poms versions

* mvn -P release versions:set -DnewVersion=1.1.0-SNAPSHOT -DgenerateBackupPoms=false  
* mvn versions:revert

* mvn --batch-mode -P release release:update-versions -DdevelopmentVersion=1.1.0-SNAPSHOT

## MacOS

### Shortcuts

* cmd+shift+3 --> saves whole screen to file on Desktop
* cmd+shift+4 --> saves selected stuff to file on Desktop
* cmd+shift+5 --> opens setting window with recording option
* ctrl+cmd+shift+4 --> copies selected stuff to Clipboard

## AWS (CLI, SDK)

### EC2
* aws ec2 start-instances --instance-ids i-0ac8092a3dc1e87d1 --region us-east-1  --> starts an instance
* aws ec2 stop-instances --instance-ids i-0bd1da4bba7cd8a94 --region us-east-1  --> stops an instance
* aws ec2 describe-instances --region us-east-1 --filters "Name=instance-id,Values=i-5ee54ba6"
* aws ec2 describe-instances --region us-east-1 --filters "Name=tag:DummyTag,Values=Shared"  --> filters out instances with tag value
* aws ec2 describe-instances --region us-east-1 --filters "Name=instance-state-code,Values=16" > running.txt  --> running instances

* aws ec2 describe-instances --filters 'Name=tag:Name,Values=dev-server-*' --output text --query 'Reservations[*].Instances[*].InstanceId'

### Security groups
* aws ec2 describe-security-groups --group-names LDAP

### LOAD BALANCER
* aws elbv2 describe-load-balancers --> describes all LBs on your account
* aws elbv2 describe-load-balancers --load-balancer-arns arn:aws:elasticloadbalanci --> describe ALB 
* aws elbv2 describe-listeners --listener-arns arn:aws:tlalal --> describe ALB listeners
* aws elbv2 describe-listeners --listener-arns arn:aws:elasticloadbalancing:us-east-1:366703173583:listener/app/LinuxClustered656-LB/ded2e0f3e2c9e3e8/c0aa6620121a7c6d --> describe ALB listeners

* aws elbv2 describe-listeners --load-balancer-arn arn:aws:elasticloadb --region us-east-1 --output json --query 'Listeners'
* aws elbv2 describe-listeners --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1 --region us-east-1 --output json --query 'Listeners[0].ListenerArn'

* aws elbv2 describe-target-groups --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:

* aws elbv2 describe-target-health --target-group-arn arn:aws:elasticloadbalancing:us-east-1:

### STACKS
* aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE --region us-east-1  --> list stacks
* aws cloudformation list-stack-instances --stack-set-name lifesaver

### S3 bucket

* aws s3 cp <file_name> s3://<bucket_name>/<folder_name>/<file_name>

* aws s3api list-buckets --query "Buckets[].Name" --> list buckets on S3
* aws s3 ls s3://pbeo-files --recursive --> list files in the folder with recursion