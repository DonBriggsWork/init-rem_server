# init-rem_server

@author Don Briggs
@date 2023-12-07

## Summary
Remotely initalize an AWS ec2 intance, and configure it as a LAMP/Laravel server.

## Overview
This utility remotely connect to an AWS ec2 instance running Ubuntu, and install and configure packages, support scripts, and additional files required to configure a newly created instance as a Laravel server. Note that this utility is intended to be used on a virgin Ubunu installation. In particular, your OS should not have any 3rd party repositories, or alternate drivers installed. This utility connects to your server remotely over SSH, pushes some files to it, and kicks off the initial upgrade. Note that the SSH connections require that you have created an 'ssh config' file in the '.ssh' directory of your home directory.  Read more about SSH config files here: https://linux.die.net/man/5/ssh_config


Host aws
    Hostname ec2-54-80-195-179.compute-1.amazonaws.com
    User ubuntu
    IdentityFile /home/dbriggs/.ssh/wgtmp.pem

## Procedure

1. Boot remote instance, and be sure that you can ssh to it utilizing the connection information in your confiuration file. (Example: ssh aws)
2. From your client, ie NOT via ssh connection to the remote server, cd to the directory containing this script and supporting files. (Example: cd ~/init-rem_server)
3. From that directory, run the script with the following command: ./init-rem_server. This create a dirctory called 'scripts' in your home directory on the remote server. It will also update the system repository indexes, and upgrade all installed packages to the latest version.
4. Once the 'init-rem_server" script has completed, reboot the remote server. All remaining steps are performed on the remote server.
5. SSH to your remote server. You should now have a directory named 'scripts' in your home directory. cd to that directory and run the 'init-server' command. This will copy some filews from the 'scripts' directory to your home directory. no need to reboot after this step
6. Now you will upgrade the server OS to version 23.10. This is kind of a major step and can take a long time. From the 'scripts' directory on the remote server type: "./upgrade-dist". Once this upgrade is complete, you will need to reboot the server again.
7. SSH to the remote server after it reboots. (Example: ssh aws). From the 'scripts' directory type: './inst-lamp' to install the LAMP stack on your server. This will install Apach2 web server, MariaDB database, PHP 8.2, and some additional things to make them all work together.