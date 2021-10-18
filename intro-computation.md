# Introduction to Computational Methods

## Outcomes

After completing this module, one should be able to: 

- articulate the difference between a static site and a dynamic site
- understand the basics of how Jekyll generates content using the Liquid templating language and data files
- be able to recognize and edit Liquid code that uses the basic computational operations to present data in different views

# Step 0. Read This Brief Introduction to Jekyll 

[Jekyll](https://jekyllrb.com/) is a static web generator that iterates over a directory of files in order to create a static website. A static site refers to a site that does not use a database to generate its content. This how the web used to work in the 90s and early 2000s. Most sites you use on a daily basis, especially social media and news/entertainment sites, are database-driven endeavors that create the site on the fly when you visit them. Jekyll creates the web site before you visit them, which makes them much easier to secure, load, and keep working. 

>>> ALERT on Iterate -- I'm going to use this word a lot, because that's what Jekyll does. To iterate means to "perform repeatedly." In our case then, Jekyll goes over the data in your site over and over, repeatedly, in order to use that data together with the templates we'll introduce soon, and thus to repeatedly create web pages featuring these templates and other repeated features (such as a header and footer).

Note that both types of web "generators" -- static and dynamic -- use the concepts we'll explain below (variables, templates, for loops, and if-then statements) to create content for their site. Jekyll just does this work before hand. It prebuilds the pages as opposed to building them on the fly (dynamically!) like Facebook, Wordpress, Twitter, etc. 

For more on Static Sites and Jekyll, see [Evan's GitHub Pages Workshop](https://evanwill.github.io/go-go-ghpages-b/content/2-jekyll.html). For our purposes, it's enough to know that Jekyll works over a series of config files, content files (mostly written in Markdown), layout and feature templates (mostly written in HTML), and data files to create websites -- and these are often generated in repositories on GitHub and published via GitHub Pages. 

So with this module, and the step by step instructions below, we hope to bring all the previous modules into focus and demonstrate some more complex computational concepts to help you better understand how everything is working. 

# Step 1. Copy this Repository

>>> If you've already completed Foundations 3 - [Introduction to Data](https://github.com/learn-static/foundations-3-data/blob/main/intro-data.md), you can  use the repository you used previously and skip steps one and two on this page. 

Copy code from another repository into your own and start editing it.

1. Make sure you're logged into your account on [GitHub](https://github.com)
2. Scroll to the top of this [foundations-4-github](https://github.com/learn-static/foundations-4-computation) repository and click the green "Use This Template" button (appears on the right side above the code area)
4. This brings you to a "Create a new repository" form. Follow these steps:
    1. In the **Repository name** text box, give your repository the name `computation-foundations`. If you'd like to create your own name for the repository, be sure to use a lowercase name without spaces or odd characters. Dashes (`-`) or underscores (`_`) are okay.
    2. Leave the **Description** text box blank, or, if you'd like, add your own description, maybe `A place to learn computation basics`. 
    3. Select the option for "**Public**" repository.
    4. Leave the "Include all branches" option **Unchecked**!
    5. Click on the green button "**Create repository from template**". This will take you to your new repository.

!["Create a new repository"](https://github.com/learn-static/foundations-4-computation/blob/main/images/new-repo-computation.png)


# Step 2. Activate GitHub Pages

Before we begin, you'll need to turn on github pages so that you can see the changes you make live on the web.  

1. On your project repository's home page, click the "Settings" button (appears on the right along the tabs above the code area).
2. On "Settings" page: click "Pages" in the left side menu.
3. On the "Pages" page: in the "Source" section, change the dropdown button from "none" to "main" (leave the folder option as "/root"), then click the "Save" button. 

Once saved, the page will refresh with an alert providing the URL where your site will appear. 
It will take a few minutes for the build to happen and your site to go live--so wait it out! 

Meanwhile, you might want to copy the URL to display on your home page:

1. Copy the provided URL.
2. Go to repository's home page.
3. On right side of the code area, look for "About" section and click on the cog icon to edit. 
4. In the "About" box, paste in your URL, then click "Save". This will make it easy to access the site in the future!

# Step 3. Use Variables

Variables are essential concepts in any computing language. They are, simply, a placeholder, that stands in for some value (a word, name, expression) that may change. 

Look up at the top-right corner of your screen. You'll see a circle representing your GitHub account with a graphic. This is the same for everyone who uses this site. So when the site is generated, the code has a **variable** in place that is able to pull in your specific image/avatar. 

Jekyll often defines its variables in a `_config.yml` file in the root of the repository. In the next activity, you'll edit the `_config.yml` file to better title this website. A yml file, like this one, is basically a list of key-value pairs. Or, in more human terms, a list of elements like name, title, location, etc. that a user can fill out and read. Jekyll then uses those values throughout the site to create content. 

***Activity***

1. Open the `_config.yml` file. 
  - *Technical Note:* A YML file is a file that lists keys and their values. So title, author, etc., but just in a textual list. The keys start on the left, and end with a colon and a space. The values are entered after that space. 
2. You'll see a number of "keys" or elements listed down the left side of the file, followed by colons. 
  - For example, the title variable looks like `title: foundations-computation` or title `title: foundations-data` if you're continuing from the previous lesson.
3. Let's change that to the title of our website. "Pets for Rent"
  - Click the pencil icon at the top right of the window (near the "Raw" and "Blame" buttons)
  - Change the title value to "Pets for Rent" 
  - Commit your change at the bottom of the page. 
4. Go refresh your web page for the repository. In a minute or so, you'll be able to visit the web page and see what's changed
  - The title of the page has changed in the nav menu at the top on all pages
  - The title at the top of the home page has changed. 
  - The title in the footer at the bottom of each page has changed. 
5. Explore how this happens in the code: 
  - Open up the file `index.html`
  - At the top, you can see this line: `<h1 class="text-center my-5">{%raw%}{{site.title}}{% end raw %}</h1>`
    - `{%raw%}{{site.title}}{% end raw %}` is the variable here. It's pulling data from the value you set in your _config.yml.
    - If you find this redundant, go ahead and just delete it, or replace `{%raw%}{{site.title}}{% end raw %}` with something else. You don't want to use curly brackets if you replace it, just text. Jekyll reads anything surrounded by two curly brackets as a variable. 
  - Now open up the `_includes` folder and then check out the `header.html` file and the `footer.html` file. 
    - Can you find the `{%raw%}{{site.title}}{% end raw %}` in these files as well? 


## Template 

A template is typically mixture of HTML elements (often with specific classes to determine their style) mixed with variables. This allows a website to build repeating elements with a minimal amount of code. 

Think of a directory with names, phone numbers, email addresses and pictures. If we can just create one template for how each person's information shows up on the page, that saves us a lot of time and coding -- and puts more emphasis on clean data then on repeated code. 

**Activity**

1. On our home page, there are several "cards" that display the animals' names, photos, and age. However, the order these elements appear seems wrong. Reorder the template in order to present the information in a more sensible order. 

(more info and screen shots about what where to edit)

## Array

You didn't know it, but you just were working with an array. An array, simply, is a list that a computer program can *iterate* over. In the case above, the computer iterated over our data, which is actually a list of lists: A list of animals, and a list of qualities for each animal, or, to put it in terms of the spreadsheet you worked in during the last module, a list of rows, and a list of cells for each row. 

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
