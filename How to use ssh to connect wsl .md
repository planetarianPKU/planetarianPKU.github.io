1.remove the default ssh service, and reinstall it.

```markdown
sudo apt-get remove openssh-server
sudo apt-get install openssh-server
```
2.remove the default config file

```markdown
sudo rm /etc/ssh/ssh_config
```
or modify the config file

```markdown
sudo vi /etc/ssh/sshd_config
PasswordAuthentication yes
```

3.start the ssh service

```markdown
sudo service ssh restart
```

Other things:
Every time I start wsl, I have to restart the ssh service, so I decided to write the command to start the ssh service into the script.

Build a new file on the terminal:
```markdown
vi startssh
```

type:
```markdown
#!/bin/bash
sudo service ssh --full-restart
```

Write and quit,and on the terminal,type:

```markdown
chmod +x startssh
```

The file then become a executable file.

And then,open:

```markdown
vi ~/.bashrc
```
type:

```markdown
#SSH
export PATH=/home/xxx/usefulbash:$PATH

```

write and quit,and type on the terminal:

```markdown
source ~/.bashrc
```

Now, you can run the script under any dictionary.

