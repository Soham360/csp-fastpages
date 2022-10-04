---
toc: true
comments: true
title: Program Design and Development Notes
layout: post
description: These are my notes on the program purpose, Collegeboard Unit 1.3
categories: [Week 6, collegeboard]
---

## The Development Process (Video 1):
All programs originate from an idea. That idea is what gives the program a certain purpose. The best way developers turn their ideas into reality is by following specific steps and stick to it. However, these steps are more of a guideline. The development of a program is a lot more exploratory and steps that you follow are dependent on what happens during development. However some steps are essential and you must do them no matter what happens.

1. First, the developers must find the problem and think about it. This is where the developers understand the requirements, constraints, and users interest. They obtain this information by creating surveys, testing users, hosting interviews, or observing others.

2. After reflecting, observing, and investigating, developers start planning how to build the program. This is when they start brainstorming ideas, planning out the code, and create a testing strategy on their work.

3. Once the program has been made, the developers talk about how the program behaves and what it should do. They will test their program with outside users. They will look back at their work to make sure it meet all the requirements and put it in a prototype. This will allow the developers to make changes while running the framework.

4. Now for the test. This might be the final step, but testing occurs during every step of the development process. Testing occurs on different levels including micro and macro. Finally, developers revisit and refine their program based on what was shown after the test, feedback provided from users, and their reflection on what they wanted the program to do.

---

## How is a Program Developed? (Video 2)
Rarely a solo endeavor

 - Usually developed by teams of people It all starts with an idea
 - Programs are developed with a specific purpose in mind
 - Developers follow specific steps and stick to their plan
 - Sometimes the development is more exploratory than anything, and the steps are dictated by what happens (both good and bad)
     - Think about early AI projects, like personal assistants Developers start investigating the problem/purpose and reflect
 - Investigation is an important step in the process
 - Developers must:
     - Determine the requirements of the program
     - Understand the constraints
     - Understand the user concerns and interests
 - How do developers investigate?
     - Surveys
     - User testing
     - Interviews
     - Direct observations After initial investigation and reflection,
 - Developers design the program by
     - Brainstorming (draw on investigation)
     - Storyboarding the program
     - Planning user experience
     - Laying out the user interface
     - Organizing into modules
     - Develop a testing strategy
 - Developers decide on the program requirements that
     - Describe how a program should behave
     - Include a list of user interactions
 - The program specifications outline all of the requirements
 - Developers create a prototype of the program (or components):
     - An incremental process is frequently used so developers can refine small parts (modules) of the program Testing, testing, and more testing!
 - Developers test the program every step of the way
 - Testing occurs at the
     - Micro level
     - Macro level
 - Developers refine and revise through testing, feedback, and reflection

 ---

## When does documentation happen? (Video 3)
Documentation happens throughout the development of the program:

 - At the beginning: list specifications
 - During: to keep track of process
 - After: to explain the overall process Documentation throughout can improve:
 - Efficiency of overall programming process
 - Programmers’ ability to test and refine the program
 - Programmers’ response to bugs

 ---

 Collegeboard quiz results

 This is the screenshot of the results of the quiz I took on Collegeboard
![]({{ site.baseurl }}/images/week6results.png)

---

## Final Project Design
### Idea/Brain Write


 - Outline and how it fits requirements
     - Program Purpose and Function -The purpose of the program is to randomly generate vocabulary words based on a definition. The program will take the user’s notes and, based on it, select the key terms and a hangman type game where it gives you a definition and you have to guess word based off it.

 - Data Abstraction
     - The program will contain lists and dictionaries. Every key term will have a definition and these will be stored in a dictionary which will be stored in a list. Or they will be stored in a local database and we will use the objects in the database to create the hangman quiz.

 - Managing Complexity
     - The dictionaries and databases will manage the complexity of the program by organizing the data inputted by the user. It will also help calling back to creating the hangman quiz.

 - Procedural Abstraction
     - 
     A function will be created to call back to the data inputted by the user. The function will iterate over the dictionary/database and use the values in them as a parameter to make a hangman quiz.

 - Algorithm Implementation
     - Like stated before, the program will contain a function that uses iteration and sequencing to make a hangman quiz based off the data inputted by the user that is saved in a database or dictionary.

 - Testing
     - The function will be called each time the user inputs a note and each time the user generates a hangman quiz. When the user inputs a note, the function is called and saves the note inside a dictionary or database. When the user presses the button that generates the hangman quiz, the function is again called and iterates through the user’s notes to generate a hangman quiz that is related to the key terms the user inputted.