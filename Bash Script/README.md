Writing Bash Script a bit different from just terminal usage. In this page, I will share some _Bash Scripting_ notes to make some people life easier.<br>
You can create your own functions via Bash Scripting which will make the Linux Usage Experience a bit better overall.<br>
So let's give some topic order and move from it.
1. First Shell Script
1. Built-in Commands
1. Variables, comments, capitalizations
1. Complicated Scripts
1. Arithmetic Operations
1. Conditional Statements
1. Loops
1. Functions and Traps

So let's have start
> First Shell Script

Shell script is working as same as the other scripting alnguage. You write your codes in related text file (_in file extansion, they usually uses .sh_).Then you execute it. Since it's linux shell language, it makes sense to work with Linux. What we are going to need is a text editor(such as __Vim,Nano, etc.__)I feel more comfortable to use Nano in my personal usage, but pick whatever you wished.<br>
__OQN__( One Quick Note): Linux shell script works with most of the Linux Distros, but use it with your own responsibilities. It may have slight changes depends on Distro and Version that you are using!
So, let's create some shell script file and filled with some codes.
~~~bash
$: nano something.sh
~~~
This line code will open an text editor and if you save your codes via pressing __CTRL + S__, it will save some file with given name (in this example it will be _something.sh_). Also, in order to quit from nano, you press the key __CTRL + X__.<br>
So what are we going to fill is simple echo programming for bash script.

    #!/bin/bash
    echo "\"If you are working on something that you really care about, you don't have to be pushed. The vision pulls you.\" — Steve Jobs"

Let's partially analyze what is written in those lines.<fr>
First, we realize that there is a symbol __#!__. This is called Shebang. This will indication for interpreter that will be execute the following codes.<br>
In this case we already clearify that path (as you can see I use full path, not relative.) with following __/bin/bash__.<br>
The following line __echo__ "__something__" is just a print function for terminal.<br>
As soon as you saved your file, you probably cannot execute it. You need to specify that the file you create should be executable.<br>
Then, you may wonder how do I check if the file executable or not. Next, if my file not executable, then how can I change it.<br>
Well glad that you asked for it. As we know from basic commands, we can list the file that placed in current directory can be listed via __ls__ command. This command has simple parameter called __-l__ to detailed list with permission/allowance of the file. Something like in picture.
![image](https://www.sumitbera.com/wp-content/uploads/2018/08/Files-permissions-and-ownership-basics-in-Linux.png)
Whenever you type __ls -la__ you will see the permission that the file you create it. Most likely, you will not see any executable permission. In order to change that, we will __chmod__ command. There are couple way to use chmod so, I will put a [link](https://www.howtogeek.com/437958/how-to-use-the-chmod-command-on-linux/) that you can follow any of it.<br>
What I am going to type is simply:<br>
~~~bash
$: chmod +x something.sh
$: ./something.sh
~~~
If you could follow until here, most likely you create and run your first bash script. Congrats!
__OQN__: The script files doesn't have to finish with _.sh_ extension, but it's good in practice. linux will not crush if you not prefer to put _.sh_ extansion, but it will make the people know that that file contains some shell script.
> Built-in Commands

Every bash command is basically commands that you could use in bash script, but in order to see if the command that you want to use is built-in or not you could check via

    $ type -a echo

in this example, you could see that we will check if the echo command is built in or not.<br>
As an output, you will see that __echo is built-in__ as well as the echo command file path like _/bin/echo_ or something similar.
> Variables, comments and capitalizations.

In shell-script, the capitalization matters! For example:<br>
WORD != Word<br>
You could test it via, trying to create two file with following name.<br>
Word.txt, WORD.txt, wOrD.txt, etc.<br>
In some OS (like Windows OS), You cannot create the following word because it's not capital sensetive.<br>
For variable description we could use 3 different character type
1. Letter
1. Underscore
1. Digit

You can use Letter and underscore in everyplace you wished, but you CANNOT start variable with digit. With in these principle, you can give any variable name you want. But make sure that the given name is clearly tell the other people its purposes.

|Correct|False|
|---|---
|SKILL|1Skill
|_Practice|Pr@ctice
|Skill2Share|??!-WTF=

Of course since you have ability to create any capitalization as you wished, shouldn't be abused. Try to follow standard coding style along with your code to easier readibility. You may want to check coding standards from the [link](https://linuxcommand.org/lc3_adv_standards.php).

|Correct|Better
|---|---
|SKILL|Skill
|sHaRe2LeaRn|Share2Learn
|T_HE_NAME|the_name
|_DO_NOT_USE_IT_STUPIDLY|_capitalNotCool

    #!/bin/bash
    Skill="Shell scripting"
    echo "I want to pracite ${Skill}. That's the topic I want to improve

In the example above, we simply used one variable called __Skill__ inside the echo function. Need to careful that, we cannot use space while we are declaring some variable like ~~Skill= "something"~~, giving spaces will throw an error. If we want to use this parameter usage with getting information from the user, then we can change our code something like this.

    #!/bin/bash
    echo "Please Type your name>>"
    read NAME
    echo "Wellcome, ${NAME}"

Another usage for variable usage could be, you type variable from terminal.

    #!/bin/bash
    echo "Wellcome, ${1}"

This line will get variable content from the cmd. Something like this:

    $ ./code.sh your_name
    > Wellcome, your_name

One Last trick that you could get your input from another command output.

    #!/bin/bash
    echo "You are now located to"
    echo "${1}"

For example, we want to redirect the output of pwd to our code

    $ ./code.sh $(pwd)
    > You are now located to
    > /wherever_you_type_the_code

Also, we will mention the parameter variable for function in up-coming chapters.

__One Quick Note__: You have to use double quote __"__ for echo in order to make ${declaration} work.~~I couldn't make the single quote __'__ work~~

Lastly for commenting something you can use hsah sign __#__ for frontside of comment. ~~I believe same as python~~

> Complicated Scripts

Before we dive into more complicated scripts, we should do pseudocoding to our algorithm/program. This step will make our creating code-blocks easier. You, as a programmer, will know exactly which step will be placed in which place/s. If you do not know what is pseudocode, I highly recommend you to search for it. It's one of essential concept for creating algorithm ~~IMO~~.<br>
Let's dive into some ~~somewhat~~ easier example.<br>
Let's write a code that will do as following
* Opening Message
* Showing Hostname
* Showing Date and Time
* Showing Kernel Information as well as architecture informations
* Show the Disk Usages
* An Ending Message

The steps are fairly simple for this example, but you may have much more application complex scripts, it's good idea to create a TODO list or pseudocode from head-start.

    #!/bin/bash

    # Opening Message
    echo "This is one of my first Shell Script"

    # Showing Hostname
    hostname

    # Showing Date and Time
    date

    # Showing kernel info with arch info
    uname -r
    uname -m

    # Showing the Disk Usages
    df -h

    # Ending Message
    echo "It iss all completed!"

Please also try the code given at below. Just copy it and place it in one file. Then give permission to be executable. Lastly, execute it!

> Arithmetic Operations

For arithmetic operation you can only use with integers, in order to use with decimal/floating points, you may need to use another (high leve) language like Python or so.<br>
For text, it's quite easy, all you have to do is typing your arithmetic operation inside the double parentheses with pref,x dollar sign

    #!/bin/bash

    echo "2 + 2 is $((2+2))"

Realize that I didn't type ~~$(2+2)~~ instead, I typed $((2+2)). The reason for that is if you wouldn't use double parentheses but use one, it will try to type as command 2+2 → which is not valid in bash.<br>
Bash need to know that it's a arithmetic operation not some sort of aliasis. That's why __IT IS CRITICAL TO USE DOUBLE PARENTHESES__<br>

|Sign|UsageArea
|---|---
|+| Addition
|-| Substraction
|*| Multiplication
|/| Division
|%| Modulo
|+=| Increment by constant
|-=| Decrement by constant
|*=| Multiply by constant
|/=| Divide by constant
|&=| Reminder by dividing with constant
|**| Exponantiation

As I mentioned above, the arithmetic operation can be done in integer, not in floats. Which means, in order to perform correct division, you will need to consider as two section

13 / 5 = 2 → How many 5 in 13<br>
13 % 5 = 3 → What is reminder after devided to 5<br>

With these information, you can get your original number as such<br>
(5 * __2__) + __3__ = 13

> Conditional Statements

One of common concept is conditional statements. You can use your conditin to run loops, make decision and more.<br>
First thing that we could check is, how many parameter is sended to script file via

    #!/bin/bash
    if test $# -ne 1
        echo "Commanded parameter is not 1"
        exit
    fi

In the code above, two unknown is placed as well as if statement opening and closing. Let start with if opening and closing.<br>
As you can see, if statement start with __if__ keyword and finish with __fi__ keyword. whatever written inside that code block, it will operate IF the given condition is true.<br>
__test__ keyword is used for testing the upcoming variable as such (the way you want it). In this usage case, __-ne__ used for _NOT EQUAL_.<br>
The Bash Script, doesn't care about indentation. But it's good practice for readable coding.<br>
For further usage and curiosity, we need to check what parameter we can use with [test](https://www.geeksforgeeks.org/shell-scripting-test-command/#:~:text=A%20test%20command%20is%20a,permissions%20related%20to%20a%20file.) command.<br>
One another way to write the conditinal state is simple not using __test__ keyword but make your statement inside the square brackets __[ ]__<br>

    #!/bin/bash
    if [ $# - ne 1 ]; then
        echo "Commanded parameter is not 1"
        exit
    fi

For correct usage, you need to give one space after __[__ and before __]__ square brackets.<br>
Some simple if - else if - else example would be like this

    #!/bin/bash
    if   [ CONDITIONAL_STATEMENT_1 ] then
        APPLICATION_1
    elif [ CONDITIONAL_STATEMENT_2 ] then
        APPLICATION_2
    else [ CONDITIONAL_STATEMENT_3 ]
        APPLICATION_3
    fi

With that, I believe I covered everything necessary for conditional statements and If usages. 

> Loops

There are two common loop that we use in our programs.
1. While Loop
1. For Loop

Let us write a simple while loop for countdown.

    #!/bin/bash

    read -p "Enter a number for countdown " COUNTDOWN
    echo

    while [ $COUNTDOWN -gt 0 ]
    do
        echo "${COUNTDOWN}"
        ((COUNTDOWN -= 1))
    done

    echo
    echo "It's counted down from ${COUNTDOWN}"

Let change this code with for loop. With slight change, instead of incrementing one by one, we increment with two. If you prefer to use 1, you can ignore the code __..2__ section.<br>
However, if you wish to change the increment value, you can change as you wish. 

    #!/bin/bash
    for count in {1..10..2}
    do
        echo $count
    done

> Functions and Traps

The usage of function/s are very common in programming, and bash scripting is not different.<br>
The idea behind to use function/s is, if you repeat your self in coding, DON'T! always remember __DRY__ → __D__ on't __R__ epeat __Y__ ourself<br>
With the understanded concepts, let's dive how to write functions.<br>
You should remember two step for functions.
1. Declarations
1. Usages

You need to declare your functions first, then use it!

    #!/bin/bash
    alert(){
        echo "**********"
        echo "$1"
        echo "**********"
    }

    alert "Warning!"
    alert "DANGER!"

As you can see here, we already called the function two times. Without using function, we need to type everything twice, which will lead to waste of time.<br>
Trap/s however different story, you can check and learn more about it in [here](https://www.linuxjournal.com/content/bash-trap-command)
