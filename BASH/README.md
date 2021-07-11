# BASH Automations

## To Create a Custom Command on Linux
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
