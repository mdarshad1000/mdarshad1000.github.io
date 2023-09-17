---
layout: page
title: Healthy Eat 🥗
description: one-stop solution to get an insight about the food you consume and discover recipes that suit our preferences
img: assets/img/healthyeats.png
importance: 2
category: latest
---
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <video controls width="100%">
            <source src="{{ 'assets/video/demo.mp4' | relative_url }}" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>
<div class="caption">
    Demo of the Ingredient parser which uses LangChain.
</div>


`Inspiration`

This app was inspired by the thousands of people that have allergies and diet restrictions and usually, people have little to no information about the food that they are consuming. Also, we haven’t come across a platform where we can find recipes that only include the ingredients we have and simultaneously take care of our diet restrictions and allergies. We have also come across many situations where we don't know the ingredients mentioned on food labels and are curious about whether they are healthy or not. So as to understand our ingredients and food better as well as to provide a place where we can find recipes that perfectly fit our preferences, we developed Healthy Eats

`What it does`

* Healthy Eats is a great resource for anyone interested in learning more about nutrition and healthy eating.
* It allows users to enter their allergies, diets, preferences, and dislikes to generate a recipe that's perfect for them. By using this app, users can stay safe and healthy by finding recipes of their favorite ingredients that accommodate their allergies and diets.
* This web app provides detailed information about the nutritional value of various ingredients.
* In addition, the website also provides a food analysis tool, which can be used to identify unhealthy ingredients in recipes and make healthier choices. It converts pictures of food ingredient labels into researched descriptions about each specific ingredient in an intuitive and readable format.

`How we built it`

* The Core of this Application is built using LangChain 🦜 and GPT-3
* Backend infra is made using Django framework.
* The frontend is using HTML/CSS/JS.
* Miscellaneous features use EdamamAPI.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/a.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/b.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/c.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     Features of the web application: Recipe Search, Calorie Calculator, Ingredient Parser
</div>
