
1. make an scrpit
for example we make a stript to start ssh service.
#open the script
```markdown
vi startssh
```
#write and quit:
```markdown
#!/bin/bash
sudo service ssh --full-restart
```
#make the script into an executable file
```markdown
chmod +x startssh
```
2. use pwd to get the path
```markdown
pwd
```
3. add the script PATH to ~/.bashrc
#open the ~/.bashrc
```markdown
vi ~/.bashrc
```
#write and quit:
```markdown
#SSH
export PATH=/home/xxx/usefulbash:$PATH
```
4. update ~/.bashrc
#input the following command on the terminal.
```markdown
source ~/.bashrc
```
5. Test
Now You can run this script named startsshh in any directory,just type:
```markdown
startssh
```
