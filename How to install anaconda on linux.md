Introduction: Anaconda has many conveniences. But you should pay attention to some details to avoid version conflicts. WSL is a linux system under Windows, which has great advantages over virtual machines.

1. Install Windows Subsystem for Linux (WSL) in the windows store.
Note: You need to enable WSL in the developer mode. After the installation is complete, replace sources.list with Tsinghua sources at https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/ to improve various download speeds.

Also remember to change to allow remote connections, so that you can use xshell to connect to WSL.

2. Enter https://repo.anaconda.com/archive/, choose the version according to whether the computer is 32-bit or 64-bit, and download anaconda for linux. I am using Anaconda3-5.2.0-Linux-x86_64.sh.

3. Enter the wget command to download in the terminal command line

```markdown
?$ wget https://repo.continuum.io/archive/Anaconda3-5.2.0-Linux-x86_64.sh
```


4. Run the downloaded script

```markdown
$ bash Anaconda3-5.2.0-Linux-x86_64.sh
```

5. You are prompted to enter yes to agree to the terms, and enter yes to agree to the installation path.

6. Prompt to install VS Code, do not install here, the download will be very slow.

7. Close the current terminal and reopen it.

8. If there is more "(base)" on the left side of the command line, and input:

```markdown
conda list
```

 it will appear:

```markdown
# packages in environment at /home/*/anaconda3:
……
```

It means it's installed properly

9.modify ~/.bashrc file

```markdown
$?vi ~/.bashrc
```

Add the following two commands:

```markdown
. /home/xxx/anaconda3/etc/profile.d/conda.sh
conda activate
```

(Change xxx in the above command to the path where you installed anaconda yourself)


10.建立环境。

The base is the basic environment, but we must not do things directly on the base, because you will find that the versions of many packages are incompatible, such as the different writing methods of numpy high and low versions. If you encounter this kind of problem, you will not only have to reinstall, but also experience a period of crash.

Therefore, we establish an independent environment for each independent project, as long as we ensure that the packages in this project are compatible.

So how to build it?

In the anaconda command line (that is, the command line with base on the left), enter:

```markdown
?$ conda create --name SUNNY?python=3
```

This command will create an environment called SUNNY and use python3.

Enter y to continue.

After installation, enter

```markdown
?$?conda activate?SUNNY?
```

You will find that the text in the leftmost bracket of the command line will change from base to SUNNY, which reminds you that this is in SUNNY and not in the base environment.

11. Conflict Warning

There are some libraries in linux, in /usr/lib, such as cmake. After installing anaconda, anaconda library is added to the system. At this time, when you are performing cmake operations, the system will report an error that there is a "conflict". This is because the compiler does not know whether to use the linux library or the anaconda library. 
We enter:

```markdown
$ echo $PATH
```

You will find the path of anaconda inside

```markdown
/home/sun/anaconda3/bin:/home/sun/anaconda3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```

Therefore, before using cmake to compile, we have to comment out the two lines of anaconda in ~/.bashrc, and then uncomment them after the compilation is complete.
Enter after the comment:

```markdown
$ echo $PATH
```

If the path of anaconda disappears, it can be compiled.



12. Install packages



```markdown
$?conda install **(package name)
```

What you need to tinker with yourself. Don't forget to create a new environment (after all, you can delete it if you break it).



13. Install jupyter notebook

Enter in the environment created by yourself：

```markdown
$?conda install -c conda-forge jupyterlab
```

Enter y to confirm. I won’t elaborate on how to use it. Anyway, it’s very suitable for WSL, because you can directly copy the given URL to your browser and program directly in the browser instead of typing in the command line.



Reference:

```markdown
https://gist.github.com/kauffmanes/5e74916617f9993bc3479f401dfec7da

https://zhuanlan.zhihu.com/p/95497832
```
