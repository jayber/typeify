# Typeify
## What is it?
Typeify is a templating tool for people who are happy to write code to create beautiful 
websites based on templates 
created by others.
## How do you use it?
1. You chose a template from those created by designers, and add it to your config.
2. You create your site by writing Typescript that uses types specified in the template.
3. You run a build command.
4. You open your site locally or on a server.

## Sounds familiar
Honestly it is, but I have found a lack of tools that really emphasize the role of 
the designer in creating great sites in a way that is easy for end users to leverage.

## So what's different?
It isn't handlebars or jade or mustache, and, if you want to use those, it shouldn't 
get in the way. Similarly, it's not react or vue or angular and should allow you to 
use these too (+ tachyons, tailwind etc.). But it isn't really about the sort of sites 
those frameworks are used for.

It's about landing page type sites with static content where you want to use an off
the shelf template created by someone who is skilled in web design without that person
having to personally hand craft your site. The "designer" can create a template, which 
they can make available for free or sell, which the "end user" can use to generate their
site, selecting options made available by the designer and adding their own content.

Typeify should be very **unopinionated**. The template you chose may be more or less opinionated.
But what you get out of it is a static site that looks great without you having to know
how to make a site look great.

## Go on...
The template defines the structure of the site. Different sorts of websites have different structures,
not just different ways of styling the same structures. A blog site is structured differently from a 
portfolio site, is different from a CV site, is different from a product site. And different designs 
will have different structures within those types. Lots of people know how to do these things, but
do **you** know, and how interested are you in learning? If you want to get on with doing something 
else, while still having an aesthetically pleasing site to tell people about it then Typeify is for you.

The "designer" creates a template. A template is a set of class definitions which define the structure
of the site the template can output, plus the styles that will be applied to the elements within
that structure.

The "end user" imports the template they want to use. This will give them a set of classes they can
instantiate in code to build a tree of instances that specify the elements that will be generated, but 
limited to what the template makes available (and is therefore capable of styling).

#### So:
The designer makes a template X which says:

sites made with this template are made up of

- a `Site` - with an optional `ColourPalette`
- each `Site` contains one or more `Pages`
- each `Page` contains one or more `Articles`
- each `Article` has a `Title`, an `Author` and a `Content`.


A `Site` will create html like this:

A `Page` will show a clickable tab

An `Article` will create an html element of "content" which will be styled like this

#### Then:
An end user says, ok lets import module X into my source file in which I specify a tree of the classes
specified in X with my content, so I create a
```
new Site(ColourPalette.ORANGE)
```
which contains one 
```
new Page("Welcome") 
```
to which I add one 
```
new Article("First article", "Professor Hubert J. Farnsworth", "In this article I will demonstrate...") 
```
and the second
```
new Article("Second article", "Phillip J. Fry", "It was the best of times, it was the blurst of times...")
```

Then end user runs the Typeify build command on their source file which will output an html
file of the above structure with the relevant style set.