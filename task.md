## CST 8254 Lab 1

> **OVERALL: just following task 1,2,3. you should be familiar with them already with knowledge from last semester tho xd. for [task 4](#task-4) i added how to access to webmin, so that you can take a screenshot of it. and for [task 5](#task-5), its updated too**

----
----


What you will do:
1. Configure your Raspberry Pi as a LAMP stack.
2. Install Wordpress on the Raspberry Pi.
3. Install Webmin on the Raspberry Pi .
4. Practice some Linux commands.

### Task 1:

1. Install Raspberry Pi OS using Raspberry Pi Imager  [https://www.raspberrypi.org/software/ 
   Select Raspberry Pi OS and recommended software from the first dropdown list.
2. If you have a keyboard, a mouse, a TV with hdmi input and access to your router, plug all the cables and proceed to step 4 with the installation.
3. If you want to do a keyboardless, screenless, wireless install:

   - Use the settings button to setup the pi name (it must be your algonquin user name). wireless settings and password.

   - If you have a windows machine, **install OpenSSH**, start Settings then go to Apps > Apps and Features > Manage Optional Features. Scan this list to see if **OpenSSH client** is already **installed**. If not, then at the top of the page select "Add a feature", then: To **install** the **OpenSSH client**, locate "**OpenSSH Client**", then click "**Install**".

   - Get the IP address of your Pi by issuing the command `ping username.local` from a Terminal window/Command prompt window.
   
   - Then issue the command `ssh pi@<ipAddressOfYourPi>` where<ipAddressOfYourPi> is the Ip obtained from the previous step.
5. Start a terminal session then type `sudo raspi-config` . Navigate the various menu options to 

   - make sure that SSH, VNC, SPI, I2C are enabled. 
   - make sure you boot automatically in the GUI using the user pi.
   - set the time zone.

### Task 2:

Install the following packages on your Pi using `apt-get`. Install them in the following order

1. Start by issuing the following commands from a terminal/command prompt window.
   `sudo apt-get update`
   `sudo apt-get dist-upgrade`

2. Apache2: `sudo apt-get install apache2 -y`

3. Mariadb: `sudo apt-get install mariadb-server`

   Once installed, issue the following commands from a terminal/command prompt window. Make sure you replace 'password' with a password of your choice.

   ```
   sudo mysql
   
   CREATE USER 'pi'@'localhost' IDENTIFIED BY 'password';
   
   GRANT ALL PRIVILEGES ON *.* TO 'pi'@'localhost';
   
   FLUSH privileges;
   
   EXIT;
   sudo service mysql restart
   ```

4. Php: `sudo apt-get install php`

5. Phpmyadmin: `sudo apt-get install phpmyadmin`
   Install it on Apache, you may need to create a password for phpmyadmin database access.

### Task 3:

Intall a copy of Wordpress on your Pi.

The following site will assist you:

https://projects.raspberrypi.org/en/projects/lamp-web-server-with-wordpress/5

When setting up the wordpress database, log on using the user you created instead of using the`root` user as specified.

### **Task 4:

Install a copy of `webmin` on your raspberry pi.

**...U SHOULD LEARN VIM BRUH...**

1. ehhhhh In a terminal/command prompt window 

   - `sudo nano /etc/apt/sources.list`
   - add the following line to the file: `deb https://download.webmin.com/download/repository sarge contrib`
   - `ctrl-o` to save the file
   - `ctrl-x` to exit

2. run the following commands:

   ```
   wget https://download.webmin.com/jcameron-key.asc && sudo apt-key add jcameron-key.asc && sudo apt-get install apt-transport-https && sudo apt-get update && sudo apt-get install webmin
   ```

3. MOST IMPORTANTLY, after installation above, this is how to access to webmin so that you could take a screenshot: 

    `sudo service webmin start` to start the webmin

    in your browser, go to `http://[YOUR_IP]:10000`. replace YOUR_IP with the result of command `hostname -I`. and you will be able to see the `username` and `password` page. the username is your hostname of your machine, and the password is the boot-up password you set, which only you know about them. after that, you will login the sysinfo dashboard! dont forget to take a screenshot kiddo

*>> if you encounter any errors in this step, be sure to leave a message&mention me in discord or send an dm <<*
   


### **Task 5:

Download the following Unix tutorial

in your pi's terminal command line, do this:

```
cd ~ && curl http://www.ee.surrey.ac.uk/Teaching/Unix/arc/unixtut.tar.gz -o unixtut.tar.gz && tar -xf unixtut.tar.gz && sudo cp -R unixtut /var/www/html
```
additionally, remove the zip: `cd ~ && rm -rf unixtut.tar.gz`


### Task 5: Checking your lab

Make a screenshot of Wordpress running, phpmyadmin running and Webmin running and upload to GitHub.

### Marking Scheme

| **Rubric** This lab has a maximum mark of 10, awarded according to the following rubric. |          |
| ------------------------------------------------------------| :------: |
| **Criteria**                                                 | **Mark** |
| Superior capability. Lab submitted meets or exceeds expected standards |    10    |
| Satisfactory capability, acceptable product/result           |    7     |
| Marginal capability, substandard product/result              |    5     |
| No capability, unacceptable product/result. Work not submitted |    0     |

Note that 40% of your final grade comes from the grades you obtained from your labs and assignments.
