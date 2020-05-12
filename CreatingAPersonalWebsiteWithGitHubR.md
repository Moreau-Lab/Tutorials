Making a Personal Website with Github and R
================

## Getting set up with Git, Github, and Rstudio:

To make your website, you’ll need to have Git installed on your
computer, connected to a Github account, and communicating with RStudio.
Follow the [lab
tutorial](https://github.com/Moreau-Lab/Tutorials/blob/master/GitGitHubTutorial.md)
to get this all set up ahead of time.

## Creating a repository for your website:

First, you will need to create a repository for your website, which will
house all of the code, images, and other files that come together to
make the site. Click the + button in the top right corner of your Github
page, and click “New Repository”.

![](./images/WebsiteRepo.png)

In order to have the cleanest url for your website, you will want to
name your repository the exact same thing as your Github username (e.g.,
I named mine "mbarkdull). This will ensure that your website url is
username.github.io. Be sure to initialize the repository with a ReadMe
so that you can clone it.

Once your repository is created, click the green Clone or Download
button, and copy the url to clone your repository.

<img src="images/CopySSH.png" width="400px" />

Open RStudio on your computer, and [create a new project initialized
from your Github
repository](https://github.com/Moreau-Lab/Tutorials/blob/master/GitGitHubTutorial.md#get-things-set-up-in-rstudio).

In order to ensure that Github pages sets your website up correctly,
you’ll need to go back to the repository on Github, and tell Github
that it should look for our website files on the master branch. To do
this, click the “settings” button in your repository, scroll down to
“Github Pages”, and select “master” under the “Source” dropdown menu.

![](images/Settings.png) <img src="images/Master.png" width="400px" />

Now we are all set up to actually add content to the website\!

## Creating Markdown files for your website:

First, make sure that you have the most recent version of rmarkdown
installed:

    install.packages("rmarkdown", type = "source")

Let’s create the basic files needed to put a website together. Open
terminal, and change directories to the directory that corresponds to
your website repository. Create the following files:

    touch _site.yml 
    touch index.Rmd 
    touch about.Rmd 

`_site.yml` is a file that tells Github how all of your website pages
will be assembled. `index.Rmd` is basically a homepage for your website.
`about.Rmd` will be an about page for the website. Go ahead and open all
of these files in Rstudio.

First, fill out your `_site.yml`; obviously, change the text to match
what you want for your website:

    name: "YOUR-WEBSITE-NAME"
    output_dir: "."
    navbar:
      title: "Your website name"
      left:
        - text: "Home"
          href: index.html
        - text: "About Me"
          href: about.html

Next we will add the minimum info to the two `.Rmd` files. For
`index.Rmd`, add:

    ---
    title: "Your website name"
    ---
    
    Hello, World!

And to `about.Rmd`, add:

    ---
    title: "About Me"
    ---
    
    Why I am awesome. 

## Turning everything into a website:

Save all of those files, and now let’s connect everything together to
form a website. First, go back to terminal and create a simple R script
file in your website directory:

    touch build_site.R

Now return to RStudio and run the command:

    rmarkdown::render_site()

This generates a file, `index.html`, that corresponds to your website\!
You can open this file up in a web browswer and see a preview of what
your website will look like.

## Getting the website online:

Now we need to take your website and put it online, so that other people
can check it out\! To do this, we need to [commit your changes and push
everything to
Github](https://github.com/Moreau-Lab/Tutorials/blob/master/GitGitHubTutorial.md#make-a-change-save-it-commit-it).

Once you’ve pushed things to Github, you’ll be able to see your website
at yourusername.github.io (be patient, it takes a few seconds for the
changes to load onto Github).
