# AUX PROJECT 1: SHELL SCRIPTING

In this project, you need to onboard 20 new Linux users onto a server. Create a shell script that reads a csv file that contains the first name of the users to be onboarded.

Connect to AWS EC2 instance and Update Ubuntu packages

Create the project folder called Shell

`mkdir Shell`

![Shell directory created](images/mkdir-shell.PNG)

Move into the Shell folder

`cd Shell`

![moved into Shell folder](images/cd-Shell.PNG)

Create a csv file name "names.csv"

`touch names.csv`

![csv file created](images/Names-csv.PNG)

Open the names.csv file and populate it with random names

`vim names.csv`

![updating names.csv](images/Names2-csv.PNG)

Now open a blank terminal and cd into Downloads (wherever your PEM key is)

Create and copy shell file to be named "onboarding_users" from local machine to the remote machine

`scp -i MyPBL.pem onboarding-users.sh ubuntu@18.216.118.114:~/;`

![scp from local machine](images/scp-from-local-machine.PNG)

Move the onboarding-users.sh file into Shell directory

`mv onboarding-users.sh /home/ubuntu/Shell`

![move the shell file into the Shell directory](images/mv-scp-onboarding-users-to%20-Shell.PNG)

Create needed private and public keys files

![created private and public keys files](images/touch-private-public-keys.PNG)

Open the public key file

`vi id_rsa.pub`

![Open public key file](images/Open-public-key-file.PNG)

Edit the public key file

![Edit public key](images/edit-public-key-file.PNG)

Open the private key file

`vi id_rsa`

![Open private key file](images/Open-private-key-file.PNG)

Edit the private key file

![Edit private key](images/edit-private-key-file.PNG)

Open and edit the onboard-users.sh file

`vi onboard-users.sh`

![Edit the onboard-users.sh ](images/edit-onboarding-users-file.PNG)

To check if you can add new developers, run

`sudo groupadd developers`

![check status successful](images/groupadd-developers.PNG)

To the onboard-users.sh file, it has to be made executable

`sudo chmod +x onboard-users.sh`

![permission status](images/adding-executable-permissions.PNG)

Switch to a super user to get into root

![admin rights issues](images/executable-permissions-confirmed.PNG)

`sudo su`

![Switch to a super user](images/super-user-mode.PNG)

Run the script again with

`./onboard-users.sh`

![successfully created new users](images/newUsers-created.PNG)

To confirm run the following command

`ls -ls`

![status confirmed](images/newUsers-created-confirmed.PNG)

To check if the developers group was created, run the following command

`getent group developers`

![status confirmed](images/developers-group-creation-confirrmed.PNG)

`cat /etc/passwd`

![developers group ID](images/newUsers1.PNG)
![developers group ID](images/newUsers2.PNG)

The "awk" command is used to filter the output from above

`cat /etc/passwd | awk -F':' '{print $1}' | xargs -n groups`

![filtered output](images/awk-filter-command.PNG)
![filtered output](images/awk-filter-command2.PNG)

To test the connectivity for the new users,create and copy the pem key into the file

`touch aux-proj.pem`

`vi aux-proj.pem`

![create and copy the pem key into the file](images/To-test-newUsers-create-private-key.PNG)

`ssh -i aux-proj.pem Tosan@18.216.183.114`

![connectivity unsuccessful](images/To-ssh-via-newUser-Tosan.PNG)

pem key is not well protected

`ls -l | grep aux-proj.pem`

![checking permissions](images/checking-grepping-output-to-aux-proj-pem.PNG)

To protect the pem key, run

`sudo chmod 600 aux-proj.pem`

![Access restricted](images/protecting-the-pem-key.PNG)

Retry connecting Tosan to the server

`ssh -i aux-proj.pem Tosan@18.216.183.114`

![connection now confirmed for Tosan](images/newUsers-Tosan-ssh-connection-confirmed.PNG)

check the user privileges for Tosan

`sudo apt update`

![check status](images/making-sure-Tosan-has-sudo-rights.PNG)

Connecting with Dayo (another new user) to the server

![connection now confirmed for Dayo](images/connection-confirmed-for-newUser-Dayo.PNG)

check the user privileges for Dayo

![check status](images/sudo-rights-status-Dayo.PNG)

The onboarding of new users is successful.
