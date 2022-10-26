So far, you should check or at least have an idea what are the basic commands, and how to write bash script in some way. If not, please check the section of __Basic Commands__ first and then, __Bash Script__ to have an idea.<br>
With that being sad, we need to understand why we need a little more advanced techniques. What are the purposes of the tools we will mention in this page.<br>
The Topics:
1. AWK
1.1 Built-in Variables in AWK
1. SED

Honestly, I didn't know these tools and usages until I create this notes. So, I may have lot of mistakes and wrong usages. Search and keep learning until find the correct way.

> AWK

I am going to leave the small history of AWK to the [geeksforgeeks](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/#:~:text=Awk%20is%20mostly%20used%20for,Aho%2C%20Weinberger%2C%20and%20Kernighan.).For further information, you are wellcome the search whatever interests you. According to __geeksforgeeks__, _AWK is mostly used for pattern scanning and processing_.<br>
So, let's dive into some basics of AWK usages in scripts.<br>
Let's create a file that has following categorized order. Later on, you may compared to storage type as your connected database or simple csv file, etc.

|Category|Product|Amount
|---|---|---
|Component|CPU|5
|Component|GPU|3
|Component|PSU|10
|Peripheral|Monitor|6
|Peripheral|Keyboard|10
|Peripheral|Mouse|15
|Peripheral|Printer|3
|Network|Router|10
|Network|Modem|15

Let's assume that, these are the simple categorized item lists in Computer storage. Now we are going to write these information to simple _storage.txt_ file as follow.

    Component CPU 5
    Component GPU 3
    Component PSU 10
    Peripheral Monitor 6
    Peripheral Keyboard 10
    Peripheral Mouse 15
    Peripheral Printer 3
    Network Router 10
    Network Modem 15

Let's assume that this file our storage file. We seperate our columns with single space. Let's start to use some awk in our terminal scripts and bash scripts.<br>
First command will be printing everything in file as follow

    $: awk '{print}' storage.txt

Let's divide this command in to the sections.
1. awk
1. '{print}'
1. storage.txt

Let's start with __awk__ → This is the keyword that we telling the terimnal or bash script that, we want to use AWK functions in our commands.<br>
Second, __'{print}'__ section. This section is simply tell a program as an parameter, we want to print the input file entirely. It can be filtered with some additional commands that i will mention later.<br>
Lastly, __storage.txt__ this is the section where we give our input file. It doesn't have to be _.txt_ extension at all but since it's common file type I prefer to save as this. As mentioned before, in Linux file extansion is just for user readability. It doesn't required at all.<br>
Okay, we understand what basic AWK command looks like. Let's use some pattern filtering with our AWK command. Let's assume that you want to filter and print only parts where category is only Peripheral.

    $: awk '/Peripheral/ {print}' storage.txt

AWK commands are case sensitive since it's comparing the data itself. So do not type peripheral but instead, type Peripheral as in stored in file.<br>
Now, this searching will apply for every columns and print the matching rows to us. For example, we want to see products have 10 unit exactly in our storage. For that, we can simply type the following code.

    $: awk '/10/ {print}' storage.txt

This will gives you a following output.

    Component PSU 10
    Peripheral Keyboard 10
    Network Router 10

This is worked because we didn't type any number in _product_name_ section. There is a better way to check this as follow

    $: awk '$3==10 {print}' storage.txt

As we can see in here, __$3==10__ is section that we filter only the third column if it's 10. We can use smaller or greater signes as well.<br>
Let's say, we want to use unit equals 10 but we do not want to show the category name of items. In that case, we need to show only second and third columns.

    $: awk '$3==10 {print $2, $3}' storage.txt

I hope it's clear as I thought so far.

>> Built-in Variables in AWK

Since I am newbie at AWK, I may miss some important that I never seen before but here are the important variables I found from [thegeekstuff](https://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/) that I think important ones.

|Shortcut|Information
|--- |---
|NR | Number of Record
|NF | Number of Field
|FS | Input Field Seperator
|RS | Input Record Seperator
|OFS | Output Field Seperator
|ORS | Output Record Seperator