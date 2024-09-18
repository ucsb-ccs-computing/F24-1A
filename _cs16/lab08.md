---
layout: lab
num: lab08
ready: true
desc: "Strings and recursion"
assigned: 2024-09-30 08:00:00.00-8
due: 2024-12-13 23:59:00.00-7
---
<div markdown="1">


# Goals of this lab
This lab will have you do programming exercises with C-strings, string class objects, recursive functions, and Makefiles. You will also get more practice writing programs from scratch with little skeleton code.

# Step 1: Getting Started

1. Go to github and create a git repo for this lab following the naming convention specified in previous labs.

2. Log on to your CSIL account.

3. Open a terminal window and log into the correct machine.

4. Change into your CS 16 directory

5. Clone your github repo in the ~/cs16/ directory. Then cd into your repo directory.

Note: Remember to push your work to github at the end of EVERY work session. 

# Step 2: Getting the starter code and writing the programs

* Navigate to your cs16 directory and clone the git repository you created
```
git clone git@github.com:ucsb-cmptgcs1a-f24/lab08_jgaucho.git
```
* cd into this new directory
```
cd lab08_jgaucho
```

* Copy the starter code by typing the following command:

```
cp /cs/faculty/richert/public_html/cs16/lab08/* ./
```

Typing the list (ls) command should show you the following files in your current directory

```
$ ls
linkedListFuncs.cpp  recLinkedListFuncs.cpp  strFuncs.h
linkedListFuncs.h    recLinkedListFuncs.h    tddFuncs.cpp
linkedList.h         strFuncs.cpp            tddFuncs.h
```

This lab will have you write two functions that are specified in strFuncs.h and two functions that are specified in recLinkedListFuncs.h. You must implement these functions in strFuncs.cpp and recLinkedListFuncs.cpp. You must follow the instructions carefully. It is not enough to pass the gradescope check as the instructor and the TAs *will* be checking your submitted code to make sure your solution is using recursion where required.

## Program to find if two strings are anagrams
 In the file strFuncs.cpp, write a function called isAnagram that takes two strings as arguments and returns a boolean true if the two strings are anagrams, otherwise it returns false. The function should not be case sensitive and should disregard any punctuation or spaces. Two strings are anagrams if the letters can be rearranged to form each other. For example, “Eleven plus two” is an anagram of “Twelve plus one”. Each string contains one “v”, three “e’s”, two “l’s”, etc. Similarly "Rats and Mice" and "in cat's dream" are anagrams of each other. You may use any of the C-string library or string class functions to complete this code. You may **not** use built-in C++ functions that we have NOT discussed in lecture. You must follow a TDD style of coding. Write your own test code in a separate file and write a Makefile to compile the code.

---
## Program to check if an input string is a palindrome

In strFuncs.cpp you are asked to a function to check if a string is a palindrome. For example: "redivide" is not a palindrome, while "detartrated" is a palindrome. Read the instructions in the file carefully to understand the constraints specified for the function. Ignore case when comparing characters of the string.

```
bool isPalindrome(const string s1);
```
The above function takes a C++ string as input and returns true if an input string is a palindrome and false if it is not. You can do this by checking if the first character equals the last character, and so on. You may choose a recursive implementation in this case, although it is not required. If you chose a recursive implementation you may or may not choose to write a helper function. You won't need a helper function is you used the substr (substring) function appropriately in your recursive calls.

## Program to recursively find the sum of elements of a linked list

```
int recursiveSum(Node* head);
```
In recLinkedListFuncs.cpp you are asked to reimplement the sum function from last week, this time recursively. If there are no elements of the list, return the value 0;

## Program to recursively find the largest value of a linked list

```
int recursiveLargestValue(Node* head);
```

In recLinkedListFuncs.cpp you are asked to reimplement the largestValue function from last week, this time recursively. For this function, you may assume that the linked list contains at least one value. 

## Step 3: Turn in your code on Gradescope

Submit all the .cpp and .h files to Lab06 assignment on Gradescope via your github repo. Then visit Gradescope and check that you have a correct score.

* You must check that you have followed these style guidelines:

1. Indentation is neat, consistent and follows good practice (see below)
2. Variable name choice: variables should have sensible names.
	More on indentation: Your code should be indented neatly. Code that is inside braces should be indented, and code that is at the same "level" of nesting inside braces should be indented in a consistent way. Follow the examples from lecture, the sample code, and from the textbook.
3. Your solution for recursiveSum and recursiveLargestValue uses recursion. You will not receive credit otherwise (even if Gradescope marks your code as correct).

Commit and push the latest version of your code on github

## Step 4: Done!

If you are logged in remotely, you can log out using the exit command:

`$ exit`
