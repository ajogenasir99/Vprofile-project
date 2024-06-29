# Vprofile-project
Repo for my Vprofile project

This project simulates the automation of web deployment
In this project we will be deploying "vprofile" a java-based website consisting of multiple services,
spread across 5 different Virtual Machines. we will be deploying this website locally in this project.

# Prerequisites
there are couple of things you will need to have on your system to test/deploy this project locally
- VirtualBox - hypervisor where you can create the Vms
- Vagrant - Vm building and managing tool.
- vagrant-hostmanager plugin - manages  hosts files in a multi-vm environment.

you can download virtualbox and vagrant easily online.
you can install the plugin using this command:-
'vagrant plugin install vagrant-hostmanager'.

# Optional dependencies
- Git bash - applications which provides your system with the functionalities of both the git version control system and the bash shell, very useful on Windows OS.

# Deployment
After downloading all your prerequisites you can now start the deployment process as outlined below
1. Create a folder for the project
2. Download all the bashscripts (.sh files) in this repo into that folder.
3. Download the vagrantfile into that folder.
4. run the vagrant up command and wait for the command to execute completely. (this will take a while!)
5. You're done!

#Validation
to validate that the site you just deployed is working fine you have to take a few steps
firstly recall there are 5 Vms, each VM provides it own functionality for the site,
db01 - database (sql), app01 - application (tomcat), mc01 - caching (memecache), rmq01 - queieing agent (rabbitmq)
web01 -  webserver (nginx). so these are all the components that make the application work. the steps to validate the
sites are outlined below.
1 - get the IP for the website (from the web01 Vm) either by checking the assigned IP on the vagrant file
or by logging into the web01 vm using this command (vagrant ssh web01) then getting the IP by running this command
ip addr show and picking the public IP.
2. Input/paste that IP in your web browser, you will be taking to the HKH Infotech website, at this point
you have validated that the webserver and appserver are functional.
3. Try to login (username admin_vp, password admin_vp)
4. you will be logged into the account at this point you have verified that the database server is functional
5. click on the all users tab on the website, click on any user, you will see a data inserted into cache write up
above the user details. go back and click on the same user again, you will see a data retrieved from cache message
so the caching is working fine.
6. Go back to the IP/welcome page, click on the rabbitmq tab, you will see a rabbitmq initiated message, this is proof
that the queueing agent is working.
7. Website validated!

That is basically it, you can reach out to me if you have any issues carrying out any of the steps.