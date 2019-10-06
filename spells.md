# Useful Spells

## Linux

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

### List files

* ls -t -> 	list files sorts last modified newest on top
* ls -tr -> same as above reversed

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

## Git

## Maven
