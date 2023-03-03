---
toc: true
comments: true
title: CPT Written Response
layout: post
description: My written response for my recipe review feature.
categories: [Week 24]
---

### Video
My video demonstration can be found below or at this [link](https://youtu.be/2OPjDXT1cYg)
<iframe width="600" height="400" src="https://www.youtube.com/embed/2OPjDXT1cYg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# Written Response
## 3a.
### 3.a.i.
This program allows users to added reviews on recipes they found on our site. They can rate the recipe out of 10 and add a short comment summarizing how they felt after creating the recipe. They can also edit the review after it has been created and also delete the review.

### 3.a.ii.
In the video, I showed the ability to search for a recipe and add a review for said recipe. I also shows the ability to edit an comment and also delete it. The program takes a rating out of 10, a short comment, and the user's name. The program then uses a POST Request to add the input to a database. It then uses a GET Request to retrieve that data and formats it into a table. After the review has been posted, there is an edit button and a delete button. The edit button allows you to edit the comment using a PUT Request. The delete button allows you to delete the review using a DELETE Request.

### 3.a.iii.
The inputs of the program are the rating, the comment, and the user's name. The program detects these inputs and returns an output by adding the user's information into the review table below the input area. The program also takes an input through the edit and delete buttons. When clicked, the edit button returns an output by enabling the ability to edit the comment. The delete button, when clicked, returns an output by deleting the review.

## 3b.
### 3.b.i.
![]({{ site.baseurl }}/images/postrequest.png)

### 3.b.ii.
![]({{ site.baseurl }}/images/getrequest.png)

### 3.b.iii.
The variable im using to represent this list is "body". "body" refers to the table and its contents. Later in the image above, "body" is POSTed to the database.

### 3.b.iv.
There are 4 variables in this code. They are uid which is the username, rname which is the recipe name, comment is the short review of the recipe, and rating which is a rating out of 10.

## 3c.
### 3.c.i.
![]({{ site.baseurl }}/images/managingcomplexity.png)

### 3.c.ii.
This program manages complexity by adding the input to a table so it is easier to read and understand. This table also includes an "Edit" and a "Delete" button to account for CRUD.

## 3d.
### 3.d.i.
![]({{ site.baseurl }}/images/usingscript.png)

### 3.d.ii.
The function is a function that reads the users input and adds it to a database.

### 3.d.iii.
The function is then called so it executes and reads the user's input and adds it to a database.
