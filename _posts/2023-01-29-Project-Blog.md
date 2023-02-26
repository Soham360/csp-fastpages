---
toc: true
comments: true
title: Project Blog
layout: post
description: My Project Blog for APCSP Trimester 2
categories: [Week 20]
---

# Overview
My job in Team ReciPies is to create a place where users can add reviews on the recipes. This will probably be a place to rate the recipe out of 5 stars and also write a comment about the recipe.

# Purpose and Function
Purpose: Show users which recipes are the best, worst, easy to follow, hard to follow, etc.
Function: Below the recipe, there will be a text box along with 5 gray stars. You would write your review in the text box and click the stars to give it a rating. Once the stars have been clicked, they will turn gold. This will be saved in the database that contains the recipe.

# Data Abstraction
The rating along with the comment will be sent through a JSON file. The information will likely be stored using key/value pairs.

# Managing Complexity
Using key/value pairs to store the rating and the comment will be managing complexity because the rating could be stored as the value while the comment is stored as the key.

# Procedural Abstraction
The process for submitting a review will be fairly simple. First you will have to be logged in. Then, you would have to write a review. Next, you would have to leave a rating out of 5 stars. Finally, the review will be sent to the admins (us) where we can approve of it or deny it. This final step will be automated in the future.

# Algorithmic Implementation
Sequencing will be used when displaying the all of the recipes to sort them from highest rating to lowest rating. This is important because it allows users to see which recipes are good and which recipes are bad.

# Testing
I'll have two tests to see the functionality of my feature.
1. I'll test to see if when I submit my review, it shows up in the database or the list.
2. I'll test to see if I'm able to view reviews sent from one device on another device.

# Create Performance Task
Each peron in our group is creating a feature for our recipe website so each person's CPT will be about their feature. All 4 features will work together and be incorporated into a larger N@TM project which is a website that suggests recipes and allows a user to filter through them and leave reviews.

# Code Plan
My recipe review feature is fairly complex and will be coded with HTML/CSS/Python or JavaScript
1. The user logs into the website
2. They click a recipe
3. They scroll down to the bottom where the recipe review section is
4. They rate the recipe out of 5 stars
5. They leave a short comment detailing why they rated the recipe they way they did
6. They submit and after the comment has been approved, it will be visible

# Video Plan
For the video, I plan to scroll through our catalogue of recipes and select one. Then, I'll show other user's reviews for that recipe. Finally, I would leave a review and show it being visible even after reloading the tab.