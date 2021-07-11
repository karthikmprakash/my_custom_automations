# BASH Automations
<details open="open">
<summary>Table of Contents</summary>
  <ol>
    <li><a href="#1-setup-python-project-folders">Setup python project folders</a></li>
    <li><a href="#2-scheduling-a-script">Scheduling a script</a></li>
  </ol>
  
</details>


## 1. Setup python project folders
This automation setups a python environment to work with by creating folders and python files including README for github 

### How to?
Firstly create a shell script with a custom command name and save it in `/usr/bin`
```bash
sudo nano /usr/bin/python_proj_directory.sh
```
and inside the `python_proj_directory.sh` paste the code below or write your custom function 
```bash
#!/bin/bash
mkdir ./images ./dataset;
touch main.py README.md;
exit;
```
after creating the bash script we need to call a function that works gloabally and runs the bash script 
Usually, the aliases are stored in a hidden file `.zshrc` in the home(~) directory of the user  
Firstly 
```bash
nano ~/.zshrc
```
paste the code below into the file
```bash
# Custom Aliases
# 1  Creating multiple folders at once for a python project
function cdir(){
/usr/bin/bash python_proj_directory.sh;
}
```

## 2. Scheduling a script

## 3. Creating a custom Service file

### To run the script on system reboot (Ubuntu)
1. Have the python application ready
2. Create a [Service File](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)
    - The file must have .service extension under /lib/systemd/system/ directory
    - ```bash 
      sudo vi /lib/systemd/system/telegram_bot.service
      ```
    - and add the following content in it. Change Python script filename ad location. Also update the Description.
    - ```bash
      [Unit]
      Description=Dummy Service
      After=multi-user.target
      Conflicts=getty@tty1.service

      [Service]
      Type=simple
      ExecStart=/usr/bin/python3 /home/user-directory/path-to-python-script
      StandardInput=tty-force

      [Install]
      WantedBy=multi-user.target
      ```
3. Enable Newly Added Service
    - Your system service has been added to your service. Let’s reload the systemctl daemon to read new file. You need to reload this deamon each time after making any changes         in in .service file.
    - ```bash
      sudo systemctl daemon-reload
      ```
    - Now enable the service to start on system boot, also start the service using the following commands.
    - ```bash
      sudo systemctl enable telegram_bot.service
      sudo systemctl start telegram_bot.service
      ```
    - Finally check the status of your service as following command
    - ```bash
      sudo systemctl status telegram_bot.service
      ```
