# Introduction to Computational Methods

## Outcomes

After completing this module, one should be able to: 

- articulate the difference between a static site and a dynamic site
- understand the basics of how Jekyll generates content using the Liquid templating language and data files
- be able to recognize and edit Liquid code that uses the basic computational operations to present data in different views

## A Brief Introduction to Jekyll 

[Jekyll](https://jekyllrb.com/) is a static web generator that iterates over a directory of files in order to create a static website. A static site refers to a site that does not use a database to generate its content. This how the web used to work in the 90s and early 2000s. Most sites you use on a daily basis, especially social media and news/entertainment sites, are database-driven endeavors that create the site on the fly when you visit them. Jekyll creates the web site before you visit them, which makes them much easier to secure, load, and keep working. 

ALERT on Iterate -- define the term and talk about its importance

Note that both types of web "generators" -- static and dynamic -- use the concepts we'll explain below (variables, templates, for loops, and if-then statements) to create content for their site. Jekyll just does this work before hand.

For more on Static Sites and Jekyll, see [Evan's GitHub Pages Workshop](https://evanwill.github.io/go-go-ghpages-b/content/2-jekyll.html). For our purposes, it's enough to know that Jekyll works over a series of config files, content files (mostly written in Markdown), layout and feature templates (mostly written in HTML), and data files to create websites -- and these are often generated in repositories on GitHub and published via GitHub Pages. 

So with this module, and the step by step instructions below, we hope to bring all the previous modules into focus and demonstrate some more complex computational concepts to help you better understand how everything is working. 

## Get the Site Running

Before we begin, you'll need to turn on github pages so that you can see the changes you make live on the web. This 

## Variables

Variables are essential concepts in any computing language. They are, simply, a placeholder, that stands in for some value (a word, name, expression) that may change. 

Look up at the top-right corner of your screen. You'll see a circle representing your GitHub account with a graphic. This is the same for everyone who uses this site. So when the site is generated, the code has a **variable** in place that is able to pull in your specific image/avatar. 

Jekyll often defines its variables in a `_config.yml` file in the root of the repository. In the next activity, you'll edit the `_config.yml` file to better title this website. A yml file, like this one, is basically a list of key-value pairs. Or, in more human terms, a list of elements like name, title, location, etc. that a user can fill out and read. Jekyll then uses those values throughout the site to create content. 

**Activity**

1. Open the `_config.yml` button. 
2. You'll see a number of "keys" or elements listed down the left side of the file, followed by colons. 
  - For example, the title variable looks like `title: YOUR SITE TITLE HERE`
3. Let's change that to the title of our website. "Dogs and Cats for Adoption"
4. Change the title, then commit your change at the bottom of the page. 
5. In a couple minutes, you'll be able to visit our web page and see the title of the page has changed. 

## Template 

A template is typically mixture of HTML elements (often with specific classes to determine their style) mixed with variables. This allows a website to build repeating elements with a minimal amount of code. 

Think of a directory with names, phone numbers, email addresses and pictures. If we can just create one template for how each person's information shows up on the page, that saves us a lot of time and coding -- and puts more emphasis on clean data then on repeated code. 

**Activity**

1. On our home page, there are several "cards" that display the animals' names, photos, and age. However, the order these elements appear seems wrong. Reorder the template in order to present the information in a more sensibl eorder. 

(more info and screen shots about what where to edit)

## Array

You didn't know it, but you just were working with an array. An array, simply, is a list that a computer program can iterate over. In the case above, the computer iterated over our data, which is actually a list of lists: A list of animals, and a list of qualities for each animal. 

**Activity**

One of the qualities that we have that would help this website are photographs of the pets. Let's add photos to the cards so that we can publish the images of all these cute pets. 

(Go through adding to the template, using the arrays used previously)

(then create a new array of colors, and use that as a cycle background for the card backgrounds)

## Conditionals

The color on those backgrounds, however, is kind of random. It's just cycling through with no logic. Let's add some logic so the colors match a quality. 

**Activity**

Figure out how to use if then to create a background based on a quality. 

## Iteration -- ForLoop

***Should this go before?***

Everything is already a forloop. 

Oh it's all so confusing. 

Repo contains:
- Explanation of what is Jekyll
- Sample data

Explore how Jekyll builds pages out of modular component parts (follow the path of a markdown file through layouts and includes)

Basic computational concepts with Liquid
- Syntax (how to write a command)
- Variables 
- Arrays
- Conditionals (flow control, if/else)
- Iteration (for loops)



Jekyll is a static site generator written in the Ruby langauge. Liquid is the templating language used by Jekyll to create data driven features. 

What is a Template? What is a templating language? 

Why do that? How do they work?

Variable - explanation

Activity: 

Array - explanation

Activity: 

Iteration - explanation

Activity:  

Conditionals - explanation

Activity: 


Put it all together, connect with the others
