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

!["Create a new repository"](https://github.com/learn-static/foundations-4-computation/blob/main/images/lesson-images/new-repo-computation_sm.png)


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
    1. *Technical Note:* A YML file is a file that lists keys and their values. So title, author, etc., but just in a textual list. The keys start on the left, and end with a colon and a space. The values are entered after that space. 
2. You'll see a number of "keys" or elements listed down the left side of the file, followed by colons. 
    1. For example, the title variable looks like `title: foundations-computation` or title `title: foundations-data` if you're continuing from the previous lesson.
3. Let's change that to the title of our website. "Pets for Rent"
    1. Click the pencil icon at the top right of the window (near the "Raw" and "Blame" buttons)
    2. Change the title value to "Pets for Rent" 
    3. Commit your change at the bottom of the page. 
4. Go refresh your web page for the repository. In a minute or so, you'll be able to visit the web page and see what's changed
    1. The title of the page has changed in the nav menu at the top on all pages
    2. The title at the top of the home page has changed. 
    3. The title in the footer at the bottom of each page has changed. 
5. Explore how this happens in the code: 
    1. Open up the file `index.html`
    2. At the top, you can see this line: `<h1 class="text-center my-5">{{site.title}}</h1>`
        1. `{{site.title}}` is the variable here. It's pulling data from the value you set in your _config.yml.
        2. If you find this redundant, go ahead and just delete it, or replace `{{site.title}}` with something else. You don't want to use curly brackets if you replace it, just text. Jekyll reads anything surrounded by two curly brackets as a variable. 
    3. Now open up the `_includes` folder and then check out the `header.html` file and the `footer.html` file. 
        1. Can you find the `{{site.title}}` in these files as well? 
        2. These two files are *Templates* that Jekyll *includes* (thus the name of the folder) on multiple pages

## Template 

A template is typically mixture of HTML elements (often with specific classes to determine their style) mixed with variables. This allows a website to build repeating elements with a minimal amount of code. 

Think of a directory with names, phone numbers, email addresses and pictures. If we can just create one template for how each person's information shows up on the page, that saves us a lot of time and coding -- and puts more emphasis on clean data then on repeated code. 

Jekyll uses the templating language Liquid to create templates. 

**Activity**

On our home page, there are several "cards" that display the animals' names, photos, and age. However, the order these elements appear seems wrong. Reorder the template in order to present the information in a more sensible order. 

>>> Remember we are working with the [pets.csv](_data/pets.csv) that was corrected in the [Data module](https://github.com/learn-static/foundations-3-data) that you may have completed previous to this module. If you did not do that module, go to the _data folder and look at the pets.csv file to get familiar with the data listed. 

1. Open the `index.html` file that can be found at the root (home page) of your repository. 
2. Find the variables `{{p.name}}` and `{{p.type}}`
    1. If you look at the web page, you can see the pet's name is below the type. Let's switch them. 
    2. Change `{{ p.name}}` to `{{p.type}}`
    3. Change `{{p.type}}` to `{{p.name}}`
3. Commit your changes at the bottom of the page. 
4. Check your site and see the change. Each pet's name should now be at the top. 
5. Let's make one more edit, to streamline the cards a bit. 
    1. Go back to `index.html` and click the pencil to start editing it. 
    2. Let's move the `{{p.type}}` to the card title line so that it looks like: `<h4 class="card-title text-dark">{{ p.name }}, a {{p.type}}</h4>`
    3. We're adding a `, a {{p.type}}` so that the type of pet will be indicated along with the pet's name. This uses some text `, a ` with a variable `{{p.type}}`
    4. Delete the `<p>`tag that formerly held the type variable. Be sure to delete the `</p>` at the end as well as the `<p class="card-text">`
6. Commit the change and check out your new cards. 

Your template should now look like this: 

```
{% for p in pets %}
        <div class="col-lg-4 col-md-6 col-sm-12 mb-2">
            <div class="card">
                <img class="card-img-top" src="{{ p.image | prepend: 'images/' |relative_url }}" alt="Image of {{ p.name }}, a {{ p.type }}">
                <div class="card-body text-center">
                    <h4 class="card-title text-dark">{{ p.name }}, a {{p.type}}</h4>
                    <p class="card-text">
                        <strong>Age:</strong> {{ p.age }} <br>
                        <strong>Owner:</strong> {{ p.owner }} <br>
                        <strong>Contact:</strong> {{ p.contact }} <br>
                        <strong>Location:</strong> {{ p.location }}
                    </p>
                    <a href="#" class="btn btn-primary">Call {{p.owner}} to Rent!</a>

                </div>
            </div>
        </div>
        {% endfor %}
```

## Array

You just were working with an array. An array, simply, is a list that a computer program can *iterate* over. In the case above, the computer iterated over our data, which is actually a list of lists: A list of animals, and a list of qualities for each animal.

To put this in terms of the spreadsheet you worked in during the "data" module, a list of rows, and a list of cells for each row. 

An array is powerful because you can sort it and use logic with it to create curated features. Let's explore some of the ways Jekyll can use the Liquid Templating language to generate and curate lists. 

**Activity**

Let's simply list how many pets are available. 

1. At the top of your `index.html` page, you'll see there's a varaible assigned to our list of pets. IT looks like this

```
    {% assign pets = site.data.pets %}
```

2. Let's list how many pets are currently available on our website by adding the following line just below the `<h1>{{site.title}}</h1>` line: 

```
    <h3>Pets available: {{ pets.size }}</h3>
```

3. Say we want to know how many of these pets are dogs and cats. We'll need to use a [where](https://shopify.github.io/liquid/filters/where/) filter in liquid to filter our array. Try adding this just below the pets available line: 

```
    <h3>Dogs available: {{ pets | where: 'type', 'dog' | size }}</h3>
```

The pipe `|` character is used in liquid to break up actions. This command is saying: 
  - go through the list of pets (which is our pets.csv spreadsheet)
  - now limit that list to just those pets whose type is listed as "dog" 
  - print out the size (number) of pets that whose type is "dog"

4. Now go through and add lines that list how many cats and parrots there are. Add the following: 

```
    <h3>Cats available: {{ pets | where: 'type', 'cat' | size }}</h3>
    <h3>Parrots available: {{ pets | where: 'type', 'parrot' | size }}</h3>
```

When you're done, your pets available section should look like this: 

!["Pets, Dogs, Cats, Parrots Available"](https://github.com/learn-static/foundations-4-computation/blob/main/images/lesson-images/pets-available.png)


5. This information could be much simpler though, don't you think. Let's see if we can get it all one line. Try to do it yourself first, by creating a parenthes and listing the number of dogs, cats, and parrots there. 

Here's how that should look: 

```
    <h3>Pets available: {{ pets.size }} ({{ pets | where: 'type', 'dog' | size }} dogs, {{ pets | where: 'type', 'cat' | size }} cats, and {{ pets | where: 'type', 'parrot' | size }} parrot)</h3>
```

## The For Loop! + If/Then Statements

Filtering out lists is a common computational practice, and the above is one way to find the count of a filtered list. But what if you wanted to, say, list the names of all the dogs available. 

To do something like this, you can a
You can also use [forloops](https://shopify.github.io/liquid/tags/iteration/) and [if/then statements](https://shopify.github.io/liquid/tags/control-flow/) to manipulate which parts of your lists get featured and/or printed on the page.

A for loop ***loops*** over an array and does something ***for*** each type of filter you request. 

Our home page uses a for loop and the template we explored above to create a card for each pet. Lets look at it

```
        {% for p in pets %}
        <div class="col-lg-4 col-md-6 col-sm-12 mb-2">
            <div class="card">
                <img class="card-img-top" src="{{ p.image | prepend: 'images/' |relative_url }}" alt="Image of {{ p.name }}, a {{ p.type }}">
                <div class="card-body text-center">
                    <h4 class="card-title text-dark">{{ p.name }}, a {{p.type}}</h4>
                    <p class="card-text">
                        <strong>Age:</strong> {{ p.age }} <br>
                        <strong>Owner:</strong> {{ p.owner }} <br>
                        <strong>Contact:</strong> {{ p.contact }} <br>
                        <strong>Location:</strong> {{ p.location }}
                    </p>
                    <a href="#" class="btn btn-primary">Call {{p.owner}} to Rent!</a>
                </div>
            </div>
        </div>
        {% endfor %}

```

You can see that it starts with a `{% for p in pets %}` command. This assigns a "p" variable to each pet as the loop is run. The variable doesn't make much difference. It just has to be consistently called. So if you wanted to change the `p` to `pet` to be more verbose, it would look like this: 

```
        {% for pet in pets %}
        <div class="col-lg-4 col-md-6 col-sm-12 mb-2">
            <div class="card">
                <img class="card-img-top" src="{{ pet.image | prepend: 'images/' |relative_url }}" alt="Image of {{ pet.name }}, a {{ pet.type }}">
                <div class="card-body text-center">
                    <h4 class="card-title text-dark">{{ pet.name }}, a {{pet.type}}</h4>
                    <p class="card-text">
                        <strong>Age:</strong> {{ pet.age }} <br>
                        <strong>Owner:</strong> {{ pet.owner }} <br>
                        <strong>Contact:</strong> {{ pet.contact }} <br>
                        <strong>Location:</strong> {{ pet.location }}
                    </p>
                    <a href="#" class="btn btn-primary">Call {{pet.owner}} to Rent!</a>
                </div>
            </div>
        </div>
        {% endfor %}
```

So the code producing the card for each pet would look differnt, but **the output would be the exact same!**

## If/Then Statements

A forloop combined with an if/then statement is really powerful way to utilize data on a website. 

If/Then statements can look at the field reference and do a specific action based on the logic included in the statement. So, for instance, if you'd like every card that features a dog to have a red background you would change the `<div class="card">` line in our template to add a bit of inline CSS if the for loop was iterating over a pet whose type was "dog": 

```
            <div class="card" {% if p.type == 'dog' %}style="background:red"{% endif %}>
```

Notice that an if statement, just like a for statement, needs to be ended with **end** statement. This is called closing a function. So `{% endif %}` closes an `{% if ... %}` statement and `{% endfor %}` closes a `{% for ... %}` statement.

The if/then statement above uses the operator `==` to say if the type is exactly dog, do this. There are a number of operators that can be used on their own and in combination. Here's a list: 

== |equals
!= |does not equal
> |greater than
< |less than
>= |greater than or equal to
<= |less than or equal to
or |logical or
and |logical and

It takes some time to get familiar with those, and many of them are meant for math type logic. In our case, for building a website, using the equals (`==`) and does not equal (`!=`) operators together with `and` and `or` is pretty powerful. 

Liquid also has an operator that's great for working with text. It's called `contains` and it helps to perform if/then statements on texts. 

So in the example above, we could have written {% if p.type contains 'dog' %}style="background:red"{% endif %} and gotten the same red background for each card for a dog. 

Let's use our activity to explore this a bit further

**ACTIVITY**

The red background is a bit much. Let's remove it by changing the  But there's a subtle change we can make that will help polish our site. 

One small detail on our cards that's bugging me is that each button says "Call ___ to Rent!" but some people's contact method is email. Let's use an If/Then statement to change that. 

1. Find the button portion of our template. IT looks like 

```
                    <a href="#" class="btn btn-primary">Call {{p.owner}} to Rent!</a>
```

***Note that the variable I'm using in this example is "p" and not "pet" -- so `{{p.owner}}` and not `{{pet.owner}}` -- if you changed the template while going through the explanations above, you can just adjust your code to use "pet" rather than p***

2. Let's add an if/then statement that will say "Call" or "Email" depending on what the "contact" field contains for each pet listing. 

   - first we have to determine what piece of text we could distinguish the two types of information we want to filter: 
   - So we ask: what could a field with an email address contain that would always differentiate it from a phone number
   - An @ sign should work! 
   - Let's try it: 

```
                    <a href="#" class="btn btn-primary">{% if p.contact contains '@' %}Email{% else %}Call{% endif %} {{p.owner}} to Rent!</a>
```

You see we've add an `{% else %}` command. This is essentially saying to the for loop that if the contact field contains an "@" write `Email`, but in any other possible case, write `Call`.

3. Now let's get a little more complicated and change the color of the button depending on the type of the pet. We will add a new if/then command for this one --> `{% elsif %}`

This command will let us add a little more logic to the forloop. We'll make the button for a dogs purple, the button for a cat yellow and the button for a parrot green, like so: 

```
                    <a href="#" class="btn btn-primary" style="background-color:{% if p.type contains 'dog' %}purple{% elsif p.type contains 'cat' %}yellow{%  elsif p.type contains 'parrot'  %}green{% endif %}">{% if p.contact contains '@' %}Email{% else %}Call{% endif %} {{p.owner}} to Rent!</a>
```

Note that I didn't have to add a final `elsif` statement for the "parrot" type because I knew that was the only one left after cat and dog. You could, however, add an elsif statement there for a parrot and continue on for any additional pet added to the array. 

## Conclusion

So we've covered a great deal of ground in this module. I hope you were able to see the logic in all of this. Remember that we are using a specific language (*Liquid*) to do make things happen on our web page with regards to lists (arrays) and templates, but these concepts -- forloops, if/then statements, templates, arrays -- are universal to all web programming languages. 

And getting to know them better can help you think about data and work with data in increasingly complex ways. 

Thank you for your time and attention and please contact Olivia at omwikle@uidaho.edu with any questions. 