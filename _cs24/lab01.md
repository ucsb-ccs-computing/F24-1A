---
layout: lab
num: lab01
ready: true
desc: "Define implement and apply a C++ class"
assigned: 2024-09-30 08:00:00.00-8
due: 2024-12-13 23:59:00.00-7
---

# Goals for this lab

By the time you have completed this lab, you should be able to

* Define a simple C++ class
* Implement a simple C++ class definition
* Test a simple C++ class implementation

We assume you already know everything that was covered in Lab00, and we will not repeat instructions given there for basic operations. This assignment must be completed individually.

# Step by Step Instructions

## Step 1a: Do some initial ONE-TIME git configurations 

* Open a terminal window. As a reminder, that's the Application Menu, then System Tools, then Terminal Window.

* In your ~/cs24 directory, type the following commands, replacing Alex Triton with your name and atriton@cs.ucsb.edu with your email address.

```
   git config --global user.name "Alex Triton"

   git config --global user.email "atriton@cs.ucsb.edu"
```

* Next, generate a private/public key pair and upload your public key to your github account. Refer to this tutorial: [https://ucsb-cs56-pconrad.github.io/topics/github_ssh_keys/](https://ucsb-cs56-pconrad.github.io/topics/github_ssh_keys/). In the process of setting up your key pair, when asked for a passphrase **just press enter**. By doing this step you will avoid having to enter a password or passphrase everytime you push your code to git.

* Clone the starter code repo from our class organization to your cs24 directory.

```
	git clone git@github.com:ucsb-cmptgcs1a-f24/cs24-s18-starter-code.git
```

Note that this repo contains the starter code for all labs and programming assignments for CS 24 (although only the code for lab01 is up to date). So, you don't have to repeat the above step in subsequent labs.

## Step 1b: Create a new repo and clone it on your local machine

* Create a repo for this lab just like you did in lab00: To do this, open a browser and navigate to [https://github.com](https://github.com). Log into your github account. From the drop down menu on the left, select our class organization: ucsb-cmptgcs1a-f24 and proceed to create a new repo using the correct naming convention. You may refer to the instructions in lab00. Also you must set the visibity of your repo to be 'PRIVATE' when creating it. We will not repeat these instructions in subsequent labs.

* Clone the repo on your local machine: Navigate to your repo on github. If your repo is named lab00_jgaucho, then you have to go to to the link:
[https://github.com/ucsb-cmptgcs1a-f24/lab00_jgaucho](https://github.com/ucsb-cmptgcs1a-f24/lab00_jgaucho). Click on the green "clone or download" button. Then click on the address of your repo.

![submit](/lab/lab01/clone-repo.png){:height="500px"}

* In your terminal navigate to your cs24 directory, then paste the address you just copied to the terminal following the git clone command. Here is an example of the steps

```
	cd ~/cs24
	git clone git@github.com:ucsb-cmptgcs1a-f24/lab00_jgaucho.git
```

* The above command will create a new directory with the same name as your git repo. Change into that directory. For our example repo we need to type

```
	cd lab00_jgaucho
```

You will write all the code for this assignment in this directory

## Step 1c: Copy the starter code to your repo

Copy the starter code to your git repo directory

```
	cp ../cs24-s18-starter-code/lab01/* ./
```
You should see two files in your current directory: rugfit1.cpp and rugfit2.cpp

## Step 1d: Push your code to github

In furture labs we will refer to all the steps in this section as "push your code to github". What we really mean is that you sync up a current version of your code with your repo on https://github.com. Follow these steps to sync the current version of your code:

* Check the status of the files that changed since the last time you synced your repo. Just type git status as follows:

```
	git status
```

You should see the following output:

```
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	rugfit1.cpp
	rugfit2.cpp

nothing added to commit but untracked files present (use "git add" to track)
```

* Now add the files that were modified since the last sync using git add

```
	git add rugfit1.cpp rugfit2.cpp
```
OR

```
	git add .
```

Type <code>git status</code> again and you should see that two files appear in green. This means they are ready to be "saved" locally as a new version of your project. 

* Save the current version of your code as follows:

```
	git commit -m "Initial version of lab01"
```

* Finally sync your latest changes with your repo on https://github.com using git push

```
	git push origin main
```

Navigate to your repo and refresh your browser. You should see the two new files that you added to your repo appear in your repo online. 

**Your code is now accessible to the CS24 teaching staff for feedback.** This is the primary reason we are using github in this class. As you write new code in your local repo, repeat the steps in this section to sync your changes with your repo on github.

## Step 3: Study a non-OO program

In the rest of this lab, you will finish writing a C++ program that uses an object-oriented (OO) approach to solve exactly the same problems that are solved by rugfit1.cpp - but first study this program to understand the problems and their non-OO solutions:

* After including the standard C++ input-output library, a utility function is defined for calculating the area of a rectangle. All other work is done inside the main function.
* All variables are declared at the beginning of main.
* The user is prompted to enter data, and the data are read into the appropriate variables.
* Calculations are performed using the area function to help.
* Results are printed.

Here is a sample run of the program :

```
-bash-4.3$ ./rugfit1
enter width and length of floor: 10.5 15
enter width and length of rug: 13.2 7.9
floor area: 157.5
rug area: 104.28
leftover rug area: 0
empty floor area: 53.22
```

Your revision of this program should operate exactly the same way. You will make the revision using the provided skeleton code in rugfit2.cpp

## Step 4: Know what it means to design an OO program

An experienced OO programmer would frown at the sight of variable names like floorWidth and floorLength, and would absolutely cringe at seeing names like rugWidth and rugLength. Such a programmer's object-oriented training would scream out the need for objects named floor and rug, each with its own width and length attributes. And although this programmer would appreciate the procedural abstraction of an area function, he or she would prefer to let the floor and rug objects calculate their own areas. In response, the OO programmer probably would decide to write a class that can represent either a floor or a rug, or any other rectangle for that matter. Then he would use objects of this class to solve problems - maybe even future problems the programmer is not facing yet.

Here are the steps necessary to achieve such an object-oriented solution:

* Write a class definition for class Rectangle. This definition includes declarations for private instance variables to store a width and a height, and declarations for public methods that can be used by programs that need Rectangle objects. This class is the abstraction (the ADT).

* Define (a.k.a. implement) the methods of class Rectangle that were only declared in the class definition. These method definitions use a special syntax that includes a "scope resolution operator" (::) to tie them to the Rectangle class. These methods implement the abstraction.

* Create and use Rectangle objects to solve problems, often just in a main function. This main function applies the abstraction.

* Discuss the meaning of these steps with your lab partner, to make sure you both understand (at least generally) what you are to do, and hopefully gain an appreciation for why you might want to do it that way.

## Step 5: Complete rugfit2.cpp

First you should study the parts of rugfit2.cpp that are complete. It consists of three main parts - and in later labs you will normally store such parts in separate files: (1) the abstraction - class Rectangle is defined; (2) the implementation - the methods of class Rectangle are defined (a.k.a. implemented); and (3) the application - the main function is defined. Your job involves additions to each of these parts.

Now it is time to edit the program with emacs or another editor of your choice. Lab00 had a link to some emacs help if you need it.

```
emacs rugfit2.cpp
```

* Make the following edits, then save, and quit the editor.

* Fix the comment at the top to show your name and the date you are doing this lab. By the way, this instruction always applies whether or not we remind you to do it in future labs or programming projects - always type your name(s) and the date at the top of all your programs.

* In the definition of class Rectangle: declare a function named area that will take no arguments and will return a double value. Make the function const - meaning it promises not to change the object on which it is called - just like the getWidth and getLength functions that are already declared in the skeleton.

* Scroll down past the end of the class definition and past the existing definitions of the constructor and four standard get and set methods, and then define the area method you declared above. Look at the other method definitions as examples for how to do it - notice they use the scope resolution operator to identify their connection to a particular class, as in Rectangle::setLength which identifies it as pertaining to class Rectangle. Return the value of length times width.

* In the main function: prompt the user for the width and length of the rug, read those two values from the user, and then reset the width and length of the Rectangle object named rug with the user's dimensions (using the rug's setWidth and setLength methods, of course). As a reminder, you use the object's name, the dot operator, and the name of the method to do such things. For example, if we wanted to find the value of the floor's width, we could do so by using the getWidth method as follows:
floor.getWidth()

* Also in main: change the two assignment statements for floorArea and rugArea to use the area method for each of the floor and rug objects.

## Step 6: Compile and run the program to test it

Use make to compile your program. Then run it to make sure everything works.Here is a test of our solution:

```
-bash-4.3$ make rugfit2
g++     rugfit2.cpp   -o rugfit2
-bash-4.3$ ./rugfit2
enter width and length of floor: 10 11.5
enter width and length of rug: 8 15
floor area: 115
rug area: 120
leftover rug area: 5
empty floor area: 0
```

If errors occur: read the error messages and try to figure out what needs changing. Don't just randomly make changes, but instead really think about the problem and how to fix it.

## Step 7: Upload your code to github one last time

Hopefully you remembered to sync your local changes to github often as you were completing the assignment.

If you forgot to do so, be sure to follow the steps in section 1d (above) to upload your final code to github


## Step 8: Submit your code to gradescope

Go to our class site on [www.gradescope.com](www.gradescope.com). Navigate to the assignment for this lab and submit your code via github just like you did in lab00.

You should see a score of 100/100 for this lab.

## Optional Extra Challenge

DO NOT CHANGE rugfit2.cpp to do these challenge problems, and DO NOT resubmit Lab01. Instead you should create copies that have different names. The problems below are just for practice - you will not turn in any of your solutions.

The current program seems incomplete in a way. It says how much bare floor space might result or how much extra rug there is, but it does not match up the width and length dimensions in any way. A nicer program would say something like "cut X from the length to fit" or "add Y more rug to the width" for instance. It seems straightforward to find two new Rectangle objects - one for excess or lacking width, and one for excess or lacking length. Change the main function (in your new copy of the program) to work this way (no need to change anything else), or do the next challenge instead.

Realize that without making any changes to class Rectangle or its implementation, you can use those parts to solve completely different problems just by changing main. For instance, first use cp to copy rugfit2.cpp to wallpaper.cpp, and then change main as follows:

* Create objects named wall and paper (in place of floor and rug, respectively), with user-entered dimensions for the wall and for a single strip of wallpaper.

* Then calculate how many strips of wallpaper are needed to cover the wall.
Notice how this problem shows that your abstraction is reusable, and it is why we normally store the abstraction in a separate file, so we can use it again and again to solve different problems.

* Modify wallpaper.cpp (from the last challenge) to account for one or more windows and/or one or more doors - just create and use some more Rectangle objects of course.

* In case you need something more to do, why not improve class Rectangle a bit? For instance, you might want a rectangle to store the locational coordinates (x, y) of one of its corners. This might help you reuse the class in a graphical application someday, or as a way to determine whether or not two rectangles intersect one another in a different type of application. Specifically, do the following:

* Add two variables named x and y to class Rectangle's private section.
Add the corresponding get and set method declarations to the public portion of class Rectangle: getX, getY, setX and setY. Note: usually we routinely provide such methods for private instance variables, unless there is a good reason not to provide such access (which does happen sometimes).

* Define the get and set methods outside the class definition - in the same way the other class methods are defined.

* Revise or replace the main function to test your new parts of class Rectangle.

* Already finished the previous challenge, and still got some time? Add an intersects and/or intersection method to class Rectangle. Then implement and test. Here are suggested method declarations:

```
bool intersects(Rectangle const &other) const;
Rectangle intersection(Rectangle const &other) const;
```

Both methods refer to another Rectangle object, and both methods promise not to change either object. The first one returns true or false, but the second one returns a Rectangle object that is the intersection (this second version presumably would return a 0-length and 0-width rectangle if the objects do not intersect).

Push your code to github, but do not resubmit to gradescope. Attempting the extra credit portion of the lab earns you star points which work in magical ways.
