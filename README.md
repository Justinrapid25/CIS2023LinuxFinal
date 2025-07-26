# CIS2023LinuxFinal
### These are the steps I took to create, maintain, and upload files into Github using git on my Linux VM.

**Step 1**: Confirmed git was installed on the system `git --version`

**Step 2**: Opened cherrytree in the background `cherrytree &` to help keep track of steps and take notes that will eventually be added into the README.md file.

**Step 3**: Next, made an account on github making sure to adhere to the instructions.

**Step 4**: After account creation, the git was configured in the terminal to include a name and an email `git config --global user.nam "NAME"` and `git config --global user.email "EMAIL"`.

**Step 5**: Confirmed configuration changes were made `cat ~/.gitconfig` which displayed the name and email provided in **Step 4**.

**Step 6**: Ran `ssh-keygen -o` to generate ssh keys so the VM can communicate with Github securely. 

**Step 7**: Once the keys were created, the `cat /directory/directory/directory/id_rsa.pub` command was executed to confirm its creation. 

**Step 8**: The public key was copied from the terminal into the github account under settings -> SSH and GPG Keys -> New SSH key

**Step 9**: At this point it was time to create a repo in github to add the bash script. A public repo was selected during the initial setup and readme was unchecked because it was going to be added manually.

**Step 10**: Following the initial setup, Github provided line by line commands to run in order to get your repo up and running. <br>
            <br>
            *Below are the commands Github provided*: <br>
            <br>
            - `echo "# CIS2023LinuxFinal" >> README.md` <br>
            - `git init` <br>
            - `git commit -m "first commit"` <br>
            - `git branch -M main` <br>
            - `git remote add origin ...` <br>
            - `git push -u origin main` <br>
<br>
**Step 11**: Checked github to confirm that the repository was up and contained the README.md file.

**Step 12**: Subsequently, it was time to work on the bash script to upload into Github using git. The bash script needs to be able to count from 1 to 50 and print it in the terminal. To add a little flare, colors were added with the numbers. <br>
<br>
*The Script* <br>

```
#!/bin/bash

#Define an array of different colors for numbers
colors=(31 32 33 34 35 36 "38;5;208" "38;5;250")
#Creating a for loop that runs 50 times, from i=1 to i=50
#Bash and Zsh will expand this into a list because of the brace expansion {1..50}
for i in {1..50}; do
  #will pick a color from the array created earlier using modulo math to cycle through them
  #The ${#colors[@]} gets the number of elements in the array, which is 8 elements
  ##The % modulo operator ensures colors repeat from the beginning after the last one
  color=${colors[$((i % ${#colors[@]}))]}

  #This will print the numbers in different colors
  ## The \e sections adds bold and the \e[0m resets all formatting so the next
  ## line is default
  echo -e "\e[1;${color}m$i\e[0m"
done
#End script gracefully 
exit 0

```

**Step 13**: Permissions were changed using `chmod u+x finalbashscript.sh` in order to execute it. Additionally, confirmed these permissions took effect running `ls -la`.

**Step 14**: The script was executed `./finalbashscript.sh` and it worked as intended.

**Step 15**: Changed the *finalbashscript.sh* to a *.txt* file by running `mv finalbashscript.sh finalbashscript.txt`

**Step 16**: Added *finalbashscript.txt* to be committed. Entered the command `git add finalbashscript.txt`. Then ran `git status` to make sure it was staged.

**Step 17**: Added file to commit with a message `git commit -m "bash script Linux CIS2023 final project"`

**Step 18**: Pushed the file to Github `git push origin main`.

**Step 19**: Refreshed Github repo in browser and the file appeared!

### This concludes the CIS 2023 Linux Final Project


