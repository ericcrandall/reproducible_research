---
title: "Grandma's Glop Recipe"
csl: molecular-ecology.csl
theme: cerulean
output:
  html_document: 
    highlight: pygments
    toc: yes
    keep_md: yes
  word_document: default
  pdf_document:
    highlight: pygments
    number_sections: yes
    toc: yes
    theme: paper
bibliography: glop.bib
---




# Prelude
Many thanks to my r-mentor [Eric Anderson](https://swfsc.noaa.gov/staff.aspx?id=740) for sharing this lesson.

![Eric Anderson](../images/Eric-Anderson-60.jpg)

This is an R Markdown document. Markdown
is a simple formatting syntax for authoring 
HTML, PDF,MS Word documents and even slideshows. For more
details on using R Markdown 
see http://rmarkdown.rstudio.com.

When you click the **Knit** button a document
will be generated that includes both
content as well as the output of any embedded
R code chunks within the document. 

We are going to go through using many of the
features of R Markdown whilst writing
up a recipe that can calculate appropriate
quantities if you want to increase
the recipe by any factor.

First, we are going to make a subsection
dedicated to grandma from whom this
recipe came.  

## Dedication to grandma {#tag-it}

This recipe came from my grandmother whom I 
always remember used to say:

> You only get to be young once,  
> But you can stay immature forever  
> --grandma


Notice in the above that we used `>` to make a
block quote and we _also_ used two spaces (which,
of course, you cannot see!) at the end of each line
to force a line break.

I leave this dedication with a picture of grandma:

![A pic of grandma](figures/Warthog4.jpg)

__Holy Oversized Image Batman__!  You have got
to be kidding me!  There
must be some way to make that image smaller.
Sadly, in this 
dialect of markdown, there is not a direct way
to do so in the _markdown_ code itself.  However,
later we will see how to do it by printing the
image from within an R code block.

We might come back to this [Dedication](#tag-it) at some point,
so we have linked it to a tag.  Note that it does not seem
you can link to arbitrary text, but you can to section headers.

# The Recipe

## The Ingredients (Static Version) 

Let's list those ingredients for a single recipe's
worth of Grandma's Glop. We call it "static"
because it applies to just a single recipe.
We will look at "automagically" doubling,
or tripling, or "pi"-ing the recipe in a
[later section](#calc-quants).

### Static List version {#static-recipe-list}
You may want to notice what happens if you don't
have two "returns" (line endings), which give you 
at least one empty line, above the "##"'s used
to make the section header---It doesn't recognize it
as a header.

Let's see, we have already seen how to make text
_italic_ and __bold__.  Did you notice how Rstudio
highlights those bits in the text editor window?
That is called "Syntax Highlighting" and it is 
super helpful.

Let's write our recipe in a list.  Be wary!  There has
to be an empty line above the list _and_ the space
after the asterisk or number is important (i.e. 
mandatory)!

* 2 cups flour
+ 4 eggs
- 1 Pound of Grandma Gorp:
    + 0.5 pounds raisins
    * 0.5 pounds cashews
    
    ```r
    # you can indent R code blocks if you want them 
    # indented to pertain to list items.
    ```

Notice, the indent level is 4 spaces.  You can use a 
`-` or a `*` or a `+` to start those list items. In
fact, you can mix and match them too, as I did, but it
is probably better to be consistent. (Use the same symbol
within a nested level and different ones between).  Hey!
did you notice the backticks (upper left of your keyboard---
same key as the tilde) around things.  Those include 
inline code-fragments---basically they get printed
out in monospaced type (any maybe in a different
color).  Super useful for variable names like
`x_data` or `y_data`.

While we are at it, let's look at what I have done with
the text in the .Rmd file (the text file).  Note that
I have put plenty of line endings in so that there are not
big long lines.  This is a good habit to get into because
git likes to look at differences between files on a line
by line basis.  If the lines are long, then it is harder
for git to reasonably merge changes. Rstudio's editor will soft-wrap the lines so that it looks like there are line breaks but there really aren't.  Like this ridiculously long line.

And do keep in mind that a blank line equates to a
paragraph break.


### Static table version {#static-table-list}

We could also have written that stuff out in a table.
There are actually lots of ways to write tables.  See
[this link](http://rmarkdown.rstudio.com/authoring_pandoc_markdown.html#tables).

What    |   How Much    |    Units
:------  | :----:  |  ----:
Flour   |     2         |   cups
Eggs    |     4         |   eggs!
Raisins |    1/2        |   lbs
Cashews |    1/2        |   lbs

 : _Whoa! that is neat, but kind of a lot of work to input.  I sure 
 wouldn't want to do that for a big table! We will investigate ways
 to automate that. Note that the colons
 dictate the alignment._


## How to make it
Once you have the ingredients, you have to prepare
the meal.  This is a great task for an ordered list:

1. Break the eggs and scramble them
1. Grind the cashews in a food mill
1. Eat the raisins to keep your energy up
   because you are going to have a lot of stirring to
   do.  Notice that you can break lines in the text
   within an item, so long as you don't leave a blank
   line.  The indenting makes the text source more
   readable but is not necessary.
1. Add cashews to eggs, stir in flour
1. Mix for 30 minutes.

Note that you can put whatever number you want in the front
and the markdown interpreter will figure out which numbers
they should be.  The numbers must be followed by a period!

## Cooking time: It's complicated

Now, the big trick to getting grandma's glop just right
is cooking it for the proper length of time.  Describing
this is going to require that we cite some literature and 
also that we write down some equations...What fun! Let's
see how we do that with R Markdown.  Cooking time $M$ (for
minutes) decreases
as the square root of the cooking temperature $T$, but increases
as the $\frac{3}{2}$-power of the elevation $a$ (for altitude), in
feet. For $300^\circ \leq T \leq 500^\circ$ and $0\leq a \leq 5000$,
cooking time is
$$
M = (20 - \sqrt{T/4}) \times \biggl(\frac{a+5000}{2500}\biggr)^\frac{3}{2}
$$
Anyone that is really interested in writing technical
mathematical documents should learn to use LaTeX directly.
Thankfully, you can imbed R code within LaTeX much
as can be done with R Markdown.

We should perhaps qualify this model with a few statements.
This model was not empirically derived by rigorous
tests, rather we guessed at it given similar work done
on cooking times of Chinook salmon at altitude [@will2014] and 
for steelhead at different temperatures [@abadia2013]. But please
bear in mind that we did not account for the issues noted
by @crandall2016 which arise while using next
generation oven technology. You can easily add citations by 
clicking "Addins" and "Insert Citations"


Clearly, it would be nice to have a table of cooking
times, $M$, for a few
values of $T$ and $a$.  Let's take $T\in\{300, 350, 400, 450, 500\}$
and $a\in\{0, 1250, 2500, 3750, 5000\}$.  Holy smokes!
There will be 25 rows in that table!
I don't want to write that by hand!

Thankfully, we can use R to do it for us.  We make a
a data frame of values, then use a nifty function `kable`
from the `knitr` package to make the table.  Get ready,
we are going to use some R:

```r
# first make the data frame
temps <- rep(seq(300,500,50), 5)
alts <- rep(seq(0, 5000, 1250), each=5)
tab <- data.frame(T = temps, a = alts, M = (20-sqrt(temps/4)) * ((alts+5000)/2500) ^ (3/2))
```
And then we print it and it looks like this


|   T|    a|        M|
|---:|----:|--------:|
| 300|    0| 32.07365|
| 350|    0| 30.11103|
| 400|    0| 28.28427|
| 450|    0| 26.56854|
| 500|    0| 24.94577|
| 300| 1250| 44.82428|
| 350| 1250| 42.08144|
| 400| 1250| 39.52847|
| 450| 1250| 37.13067|
| 500| 1250| 34.86277|
| 300| 2500| 58.92305|
| 350| 2500| 55.31749|
| 400| 2500| 51.96152|
| 450| 2500| 48.80953|
| 500| 2500| 45.82830|
| 300| 3750| 74.25153|
| 350| 3750| 69.70801|
| 400| 3750| 65.47900|
| 450| 3750| 61.50704|
| 500| 3750| 57.75026|
| 300| 5000| 90.71797|
| 350| 5000| 85.16685|
| 400| 5000| 80.00000|
| 450| 5000| 75.14719|
| 500| 5000| 70.55728|

 : Cooking times, $M$, at various temperatures, $T$, and elevations, $a$.


## Calculating Recipe Quantities {#calc-quants}

This could be done several ways, but let us
simply look at how we would list the ingredients.

First, make an R code block where we declare
the quantities:


```r
amts <- c(Flour = 2, Eggs = 4, Raisins = 0.5, Cashews = 0.5)
mult <- 40 # make a mult-fold version of the recipe
aa <- amts * mult
```

Then access those variables inline in the list.  For example:
In order to make 40 times the standard recipe, you will
need

* 80 cups flour
* 160 eggs
* 40 lbs of Grandma Gorp:
    + 20 lbs raisins
    + 20 lbs cashews
    
And, if you want to make $\pi$ times the standard recipe
you need:



* 6.2831853 cups flour
* 12.5663706 eggs
* 3.1415927 lbs of Grandma Gorp:
    + 1.5707963 lbs raisins
    + 1.5707963 lbs cashews

Of course, had we wanted to, we could have stuck that
in a `kable` table, too.

# More notes about markdown

## A note about citations and references

You can define
different styles in a "CSL" file which you can put where Rstudio
can find it (in your project) and then call it out in the YAML
header.  You apparently can store your citation database in 
many different ways.  I chose BibTeX because that is what I am
used to.  The citation data base for this document is `blop.bib`
which looks like this:


```
@article{will2014,
  title={A comparison of cooking times for {C}hinook salmon in the {C}alifornia {C}urrent and at higher elevations},
  author={Satterthwaite, William H and Mohr, Michael S and O’Farrell, Michael R and Anderson, Eric C and Banks, Michael A and Bates, Sarah J and Bellinger, M Renee and Borgerson, Lisa A and Crandall, Eric D and Garza, John Carlos and others},
  journal={Transactions of the American Fisheries Society},
  volume={143},
  number={1},
  year={2014},
  publisher={Taylor \& Francis}
}


@article{crandall2016,
  title={Next-generation oven technology and its impact on cooking times for {G}reen {S}turgeon},
  author={Crandall, Eric D and Skaug, Hans J and Barshis, Daniel J},
  journal={Molecular Ecology},
  volume={23},
  number={3},
  pages={502--512},
  year={2016},
  publisher={Wiley Online Library}
}


@article{abadia2013,
  title={Large-scale parentage analysis reveals reproductive patterns and variation in cooking times for steelhead ({\em Oncorhynchus mykiss})},
  author={Abadia-Cardoso, Alicia and Anderson, Eric C and Pearse, Devon E and Carlos Garza, John},
  journal={Molecular Ecology},
  volume={22},
  number={18},
  pages={4733--4746},
  year={2013},
  publisher={Wiley Online Library}
}

@article{boughton2009spatial,
  title={Spatial patterning of habitat for Oncorhynchus mykiss in a system of intermittent and perennial streams},
  author={Boughton, DA and Fish, H and Pope, J and Holt, G},
  journal={Ecology of Freshwater Fish},
  volume={18},
  number={1},
  pages={92--105},
  year={2009},
  publisher={Wiley Online Library}
}
```

Note that by default only the citations in your
data base that actually got cited will be included
in the References.

It should be pointed out that you can easily grab
BibTex-formatted citations from [Google Scholar](http://scholar.google.com).

If you want to use a different bibliography style, browse
the styles available at [Zotero Style Repository](https://zotero.org/styles).
You can just download them and put them in your project.
If we have time, we can try using the _Science_ citation style.

Much more about citations with R markdown can be found 
[here](http://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html)
and you can find plenty of other good links at the bottom
of this [page](http://rmarkdown.rstudio.com/).

## Making PDF and Word documents

To make a PDF document you need the TeX typesetting engine.
It is free, but many of you probably don't have it yet.

To make a Word doc, click the down triangle to the right of
"Knit HTML" and choose "Knit Word".  Can you figure out what
changes in the document? (Again, it is textual and transparent!)
Contrast that to the Word document itself---do this at your Unix
command prompt (in the right directory of course):
```
cat auto-recipe.docx
```

### Changing styles and templates

Wanna have a different look?  Try the "Gear" link to the
right of the "Knit HTML" button.  Notice how changes there
change things in the YAML header. 

You can also check out [different YAML themes](https://www.datadreaming.org/post/r-markdown-theme-gallery/)

And let us thank fish [@boughton2009spatial]




## References
