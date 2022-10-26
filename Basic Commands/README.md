In this part of examples, I will use the Ubuntu OS (20.04). The thing I mentioned in here may change in time, so use it with your own responsibilities.<br>
_I just share the thing I know for educational purposes_<br>
With that being sad, let's understand what is Linux Commands and Where we are going to use for it.<br>
There is a [official ubuntu tutorial](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview) that you can follow and simply learn along with the way. With every ~~non important~~ details given, we can start.<br>
We type our linux commands into special windows called __Terminal__<br>.![image](https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/2X/b/ba76cbf3dc8dc2cc94d26dd61c7aad3cedcd5102.png)
<br>The terminal may look different depends on your Linux Distribution. This is not core Linux Notes, so I will not explain for every individual Linux Distros ~~Shortcut for Distributions~~. To open up Terminal, you can press the keys combination of __CTRL + ALT + T__ at the same time. This may not be created as shortcut in your Linux Distro. If that the case, I highly suggest you to search for it, it wouldn't be that hard.<br>
Inside the picture, you can see that there are some information as soon as you open it, let's have a look at what are those.
- Mark
- Linux-desktop
- ~
- $

Briefly speaking, First information that you get before __@__ sign is current user that you connected to terminal. In this example the user called "mark". The second information we could see is the desktop name called "linux-desktop". The desktop name is usually not useful as much as the other informations, that's why some Linux Distros may not show it. But depends on your application, you may find it useful. Third information we get is "~" tilda sign. This means, you are located in your home folder. We will explain what is folder and how we are switch those in upcomming section. Last but not least, the dollar "$" dollar sign. This is representation of user will type some code in terminal.<br>
After understand the basic concepts of terminal view, let's dive into some codes.<br>
Since we already talked about folders and locations, let's have a look at related commands first.<br>
|Syntax|Description
|---|---
|pwd|Current directory (or folder that you are in) viewer
|cd| Change directory
|mkdir| Make directory
|rmdir| Remove directory
|ls| Listing all the files and directories.<br>
Example usage:
~~~bash
your_username@your_computer_name:~$ pwd
/your_computer_name/your_user_name
~~~

As we can see, the directory/folder applications are straightforward to apply.<br>
Now Let's have a look at the file applications.<br>
It's worth mention that, there are simple way to create file by using __>__ operation directly, but I ~~usually~~ prefer to use a text editor to create, and manually type whatever I want to type inside the file. But you can directly create the file output via using __>__ leading opeartion. ~~may called something different then leading operation~~
~~~bash
user@desktop:~$ echo "testing text" > test.txt
~~~
Let's assume that you already type the simple command code that written below, based on this step.<br>
|Syntax|Description
|---|---
|touch| Creating File
|cat| Print the content of file
|file| determines the content type in file
|cp| Copy the file
|mv| Moving file
|rm| Remove file

Well as you can see these are the basic file operations. In order to have control over the file, we prefer to use something called __Text Editor__. Common examples would be __Vi/Vim, Nano, Gedit, etc__. You may prefer according to your taste.<br>
~~I know that Vim is very powerful but not straightforward as Nano. So, it's much of an taste matter~~<br>

So, let's assume that you already create the file _test.txt_ with the line that written on below. How about if you want to change the name of the file. You can use mv command to make it happen.
~~~bash
user@desktop:~$ mv test.txt 1.txt
~~~
With this simple line code, we simply said that, move the _test.txt_ to _1.txt_<br>
But you should remember that, if you want to change the directory and all the stuff, you should give either relative or full path of the directory.<br>
The code that we type is getting relative path, since we didn't clearified anything front of the _.txt_ files, it assumes that we want to take action with name of those files inside the current directory we are in.<br>
There is special command that is stands for manual. __man__ command is used for monitoring the detailed manual of relative command if it's written any.<br>
Example:
~~~bash
$: man pwd
~~~
In order to get out from window, just simply press key __q__. Also, the page is interactive, which mean you have control with arrow keys in your keyboards.<br>
Here is some more commands that will make your life easier when you using terminal.
|Syntax|Description
|---|---
|find| advanced searching command
|grep| Grep is used for grabbing information that you seeking for from bunch of information. It's clear when you use it.
|sudo| SuperUserDO
|df| System Disk Usage
|du|Disk Usage of file or directory
|head| File context viewer for first couple lines.
|tail|File context viewer for last couple lines. Also you can use tail command for live view with advanced parameters.
|diff| It will show the two different files lines that does not match up!
|tar|tarball is one of the most used archiver tools in linux.
|chmod| change the mod of file
|chown| change the owner of file
|jobs| display the current jobs along with their statuses
|kill| the command used for terminate the job/program
|ping|Ping command is used for connectivity status between your computer and target.
|wget| This one is used for getting internet informations, like download from link
|uname|Printing detailed information about your linux system
|echo| Used for printing text in terminal
|zip/unzip| Like tarball, this one is another common archiver.
|useradd| Adding new user to your desktop environment
|userdel| Deleting user from your desktop environment
|top| This one is like task manager in windows.
|ifconfig| Information about your ethernet connection/s
|date| Printing information about current date
|history| this one will print every command that has been entered by that user inside that terminal
|clear| Clear the screen (alternatively press __CTRL + L__)
|cal| Printing Calender
|less| Another tool for showing content of the file. You also have control with arrow too.
|ps| Process Status, you could monitorize the processes and status

These are commands that I remembered so far that almost every Linux user oftenly. Ofcourse there are more commands that can be installed via your download manager and make your linux usage much easier or much fun experienced.<br>
There are couple more trick that I need to mention in this page.<br>
First is, pressing __TAB__ key. It is used for automatically complete missing part for your line.Let's say you want to write __ifconfig__ but you are not sure about how its written. So basically, you can do is typing __ifc__ and then press __TAB__ key to automatically complete the word. If there are more than one option, like let say you wanna type option_1 but there are also option_2 and option_3. it will not automatically __opt__ and __TAB__. Instead, it will show you the options, and you will complete as follows.<br>
Second, There are concept called wildcards and regex (Regular Expressions). I am not going to dive into it. Instead i will give an [article](https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm) for you to understand the basics of wildcards.<br>
Lastly, if you type any command with __&__ sign, it will execute but it will make your terminal avaliable still. Let's say you open a file with gedit, it will allow you to use same command terminal still.<br>
    $: gedit somefile &

This page will be filled along with my gained experinced. I have plan to share specific commands just related to ethernet/internet interfacing, more control over terminal etc.