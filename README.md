# Aux-Project-1

Shell Scripting

In this project, you need to onboard 20 new Linux users onto a server. Create a shell script that reads a csv file that contains the first name of the users to be onboarded.

The script you created should read the CSV file, create each user on the server, and add to an existing group called developers (You will need to manually create this group ahead).

Ensure that your script will first check for the existence of the user on the system, before it will attempt to create that it.

Ensure that the user that is being created also has a default home folder

Ensure that each user has a .ssh folder within its HOME folder. If it does not exist, then create it.

For each user’s SSH configuration, create an authorized_keys file and add ensure it has the public key of your current user.

Before Deploying your script, you will need to update your current user with the correct public key and private key.

Test a few of the users randomly, and ensure that you are able to connect to the server using the private key and the public key.
