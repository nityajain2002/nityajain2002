<<<<<<< HEAD
# Dev Portfolio

🚀 **[Dev Portfolio V2 has arrived. Meet Devfolio, a modern portfolio + blog template built with GatsbyJS and TailwindCSS](https://github.com/RyanFitzgerald/devfolio)** 🚀

This repo contains an easy-to-customize personal dev portfolio template that was created with Sass and JavaScript. It is lightweight and fully responsive, as well as comes with the Bootstrap grid system and loaded with Font Awesome. The site is static and comes production ready if you just want to add your information and go. Alternatively, you can edit styles, colours, and scripts fairly easily. The site was built as modular as possible to make it easy to shift around styles and content.

To view a live demo, [click here](https://ryanfitzgerald.github.io/devportfolio/).

Looking for a blog template? Checkout [DevBlog](https://github.com/RyanFitzgerald/devblog).

## Features

* Gulp ready (compiles Sass and minifies JS)
* Sass ready with lots of commenting
* Fully responsive
* Comes with Bootstrap grid system
* Easy colour changes can be done through simple variable edits

## Contents

- [Setup and Configuration](#setup-and-configuration)
    - [Making Edits / Customizing the Template](#making-edits--customizing-the-template)
    - [Using the Template As Is](#using-the-template-as-is)
- [Customization and Editing](#customization-and-editing)
    - [General](#general)
    - [Images](#images)
    - [Header Section](#header-section)
    - [Lead Section](#lead-section)
    - [About Section](#about-section)
    - [Experience Section](#experience-section)
    - [Education Section](#education-section)
    - [Projects Section](#projects-section)
    - [Skills Section](#skills-section)
    - [Contact Section](#contact-section)
    - [Footer Section](#footer-section)
    - [Optional Sections](#optional-sections)
- [Changelog](#changelog)
- [License](#license)

## Setup and Configuration

The setup required can be broken into two types:
1. If you want to make edits or customize the template
2. If you just want to add your information as use as is

### Making Edits / Customizing the Template

To setup, simply fork the repo and run `npm install` in order to get all the Gulp dev dependencies. Next, run `Gulp watch` to compile the Sass and minify the JavaScript. Alternatively, if you don't have Gulp installed globally, you can run the npm script `npm run watch`. Any changes done to the JavaScript (js/scripts.js) or Sass (sass/styles.scss) will be autocompiled and ready to go.

All scripts are within `js/scripts.js` and get minified to `js/scripts.min.js`. All styles are in `sass/styles.scss` and get compiled to `css/styles.css`. Both the minified scripts file and compiled CSS file are what is loaded on the page by default.

At this point, the page is ready to go and you can begin to add your own information and make any needed changes. The sections below  contains a quick breakdown of each of the default sections and how they work.

### Using The Template As Is

If you wish to use the template as is (i.e. how it's seen in the demo), then all that's required is the `css`, `images`, `js`, `libs` folders and the `index.html` file. You would then add your content to `index.html` as needed and you're good to go!

## Customization and Editing

### General

In general, most styles on the page are based off the definitions of variables in the variable section of the style sheet:

```SCSS
// Define base and accent colors
$base-color: #3498db;
$base-color-hover: darken($base-color, 10%);

// Define background colors
$background: #fff;
$background-alt: #f2f2f5;

// Define border colors
$border: #dcd9d9;

// Define text colors
$heading: #374054;
$text: #74808a;
```

If you wish to change the general colour scheme of the page for example, simply change the value of `$base-color`.

There is also a number of default CSS classes that can be applied such as `.shadow`, `.shadow-large`, `.btn-rounded-white`, and various others. These can be found under the General Styles section in the style sheet.

### Images

By default, the template comes with a number of images, some of which can be kept and others which act simply as placeholders and should be switched. The template contains the following:

* Main background (images/lead-bg.jpg) - this is the main background image provided via [Unsplash](https://unsplash.com/). This can be kept or changed easily by replacing `images/lead-bg.jpg` with your new background (recommended size of at least 1920x1080).
* Favicon (/favicon.ico) - this is the favicon used for the page. Similar to the main bg, this can be kept or changed easily by replacing the `favicon.ico` with your new one.
* Project image - these are the images associated with the projects under the project section. These are simply placeholders and should either be replaced or removed.

### Header Section

The header section can be found within the `<header>` tag and simply contains an unordered list of anchors to different sections of the page. If you add a new section and want to be able to quickly navigate to it from the top, simply add another list element with an anchor that has the href of the ID of the section. Conversely, if you remove a section, don't forget to remove the associated navigation element.

If you wish to add a header link to an external page, simply add the class `no-scroll` to the anchor. For example:

```HTML
<li>
    <a href="https://google.com" class="no-scroll">Google</a>
</li>
```

If you wish to have a sticky (fixed) header, you simply need to add a class of `sticky` to the main header. For example, that would be accomplished as follows:

```HTML
<header class="sticky">
    <!-- Header content -->
</header>
```

### Lead Section

The Lead section is pretty straightforward, it contains an h1 for your name and an h2 for your title. It also contains a link that can be used to link to your resume should you wish to add it as well.

If you want your resume to automatically download when the button is clicked instead of opening up in another tab (the default behaviour), add the following code (Thanks to jkfran for the suggestion) in the lead:

```HTML
<a href="path/to/resume.pdf" download="resume.pdf" class="btn-rounded-white">Download Resume</a>
```

The href attribute points to where your resume is stored and the download attribute is what triggers the download / provides the name the file will be downloaded as when the user clicks the button (In this case, it will download as resume.pdf).

### About Section

The about section contains a quick about blurb that can be edited by changing the text within the paragraph tags.

### Experience Section

The experience section creates a vertical timeline with all your relevant experience. The code for the timeline creation can be found within `js/scripts.js` and is an adaptation of [RyanFitzgerald/vertical-timeline](https://github.com/RyanFitzgerald/vertical-timeline).

The default format is as follows:

```HTML
<div id="experience-timeline">
    <div data-date="September 2015 – September 2016">
        <h3>Employer Name</h3>
        <h4>Job Title</h4>
        <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur in iaculis ex.
        </p>
    </div>
</div>
```

The data attribute `data-date` is what is used to add a date to the associated timeline point. All that is really required is a wrapping div (i.e. `#experience-timeline`) and nested divs to build the timeline. The h3, h4, and p tags are optional and the contents of the div can be styled however you wish.

To add an additional section, simply add additional nested divs under the main wrapping div.

### Education Section

The Education is just a series of `.education-block` classes with some details associated with them. By default, it shows school name, date, degree, and some additional details. For example:

```HTML
<div class="education-block">
    <h3>University of Ottawa</h3>
    <span class="education-date">Sept 2016 - Sept 2017</span>
    <h4>Bachelor of Science in Computer Science</h4>
    <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur in iaculis ex.
    </p>
</div>
```

To add additional section, simply add additional `.education-block` elements.

### Projects Section

The Project section contains a number of `.project` elements that represent each of your projects. By default, it contains a 300x300 image under `.project-image` and relevant project information under `.project-info`. An example is as follows:

```HTML
<div class="project">
    <div class="project-image">
        <img src="images/project.jpg" />
    </div>
    <!-- End .project-image -->

    <div class="project-info">
        <h3>Project Name Here</h3>
        <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur in iaculis ex.
        </p>
        <a href="#">View Project</a>
    </div>
    <!-- End .project-info -->
</div>
```

If you want to hide some projects by default, you can throw them in an additional row and add the markup for the "Show More" button. This would be done as follows:

```HTML
<!-- Projects Above -->

<a id="view-more-projects" href="#">View More Projects</a>
<div id="more-projects" class="row">
    <div class="project shadow-large">
        <div class="project-image">
            <img src="images/project.jpg" />
        </div>
        <!-- End .project-image -->
        <div class="project-info">
            <h3>Project Name Here</h3>
            <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur in iaculis ex. Etiam volutpat laoreet urna. Morbi ut tortor nec nulla commodo malesuada sit amet vel lacus. Fusce eget efficitur libero. Morbi dapibus porta quam laoreet placerat.
            </p>
            <a href="#">View Project</a>
        </div>
        <!-- End .project-info -->
    </div>
    <!-- End .project -->
</div>
```

This will add a link that says "View More Projects" under the current projects and when clicked, all projects in the "More-projects" div will be shown. This is optional functionality and isn't provided by default. It is important that you keep the wrapping div ID intact ("#more-projects") as well as the anchor ID ("#view-more-projects"), however the contents of the div and the anchor text itself can be edited however you like.

#### Projects without images

If you do not wish to have a project image associated with a project, you can simply add `no-image` as an additional class to the project. It would look like the following:

```HTML
<div class="project no-image">
    <div class="project-info">
        <h3>Project Name Here</h3>
        <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur in iaculis ex.
        </p>
        <a href="#">View Project</a>
    </div>
    <!-- End .project-info -->
</div>
```

### Skills Section

The Skills section is simply an unordered list that spits out a "Skill Cloud" with all the skills listed. To add / remove skills, simply edit or add list elements, like so:

```HTML
<ul>
    <li>JavaScript</li>
    <li>Python</li>
    <li>Ruby</li>
    <li>Go</li>
    <li>Node.js</li>
</ul>
```

### Contact Section

Since the page is static, I opted to use the awesome Formspree to allow for a contact form without the need for anything else. To use it, you must have the page hosted on a server (loading a basic HTML page won't work) where a referrer header is generated. Also, simply add the email to the action. An example is as follows:

```HTML
<form method="POST" action="https://formspree.io/email@email.com">
    <input type="hidden" name="_subject" value="Contact request from personal website" />
    <input type="email" name="_replyto" placeholder="Your email" required>
    <textarea name="message" placeholder="Your message" required></textarea>
    <button type="submit">Send</button>
</form>
```
For more information on configuration of the contact form or dealing with errors, check out [Formspree](https://formspree.io/).

For a quick tutorial about formspree, check out this [tutsplus tutorial](https://webdesign.tutsplus.com/tutorials/quick-tip-add-a-formspree-form-to-your-static-sites--cms-23870) that covers different aspects and features of the form tool.

### Footer Section

The Footer contains an optional copyright where you can place your name as well as an unordered list of all of your social or coding related profiles. By default it contains Github, Stack Overflow, Facebook, Twitter, and Google Plus. You can add or remove them easily and simply use the Font Awesome icon associated with the social profile you wish to use. For a list of all icons, [click here](http://fontawesome.io/icons/).

### Optional Sections

The template comes with an optional section that can be added to the page markup to list things like Certifications, Hobbies, and more (Note: these are not included by default). The markup for the additional optional section is as follows:

```HTML
<div class="optional-section background-alt">
    <h2 class="heading">Section Name</h2>

    <div class="optional-section-block">
        <h3>Some content title</h3>
        <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur in iaculis ex. Etiam volutpat laoreet urna. Morbi ut tortor nec nulla commodo malesuada sit amet vel lacus. Fusce eget efficitur libero. Morbi dapibus porta quam laoreet placerat.
        </p>
        <ul>
            <li>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            </li>
            <li>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            </li>
            <li>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            </li>
        </ul>
    </div>
    <!-- End .optional-section-block -->

</div>
<!-- End .optional-section -->
```

You can copy .optional-section-block for each new item you wish you have in the optional section. Also, the background-alt class may need to be removed depending on where the optional section is placed in your layout as this adds the grey background. If you play it at the bottom after "Skills", it can be used as is. Also, by default the border is applied at the top, but this can also be adjusted as needed.

The optional section blocks have styling for h3 (the block title), h4, p, and ul tags by default.

## Changelog

### 1.2.2

* Updated dependencies and gulpfile

### 1.2.1

* Updated dependencies and gulpfile
* Added `no-image` optional class for projects without images (see above for usage)

### 1.2.0

* Added support for optional "Show More Projects" that hides some projects by default if included
* Added optional sections to display certifications, languages, etc.

### 1.1.3

* Added default favicon to be used or changed
* Added `sticky` class to make header fixed
* Updated docs to add image section

### 1.1.2

* Added `no-scroll` class option to header navigation anchor if you want to link to external site
* Changed contact form input / textarea colours to be based off `$base-color`
* Changed main background to 100vh so it doesn't overflow if viewport height < 700px

### 1.1.1

* Made input placeholder text more readable
* Removed timeline line when no JS
* Added some basic styling to timeline when no JS

### 1.1.0

* Fixed menu toggle on mobile devices
* Fixed z-index / scrolling issue with mobile menu
* Mobile menu now closes once a nav element is hit

## License

Completely free (MIT)! See [LICENSE.md](LICENSE.md) for more.
=======
# CSE 146 Labs

Throughout the labs in this course,
you will be working with assignments distributed as iPython notebooks and submitted to an "Autograder"
which can automatically grade some portions of your assignment.
This document will serve as a reference for the intended environment and workflow for these assignments.

Specifically, this workflow requires you to:
 - Obtain your homework assignments (comprising iPython notebooks, tests, and supplementary files) by cloning private git repositories.
 - Open and edit the provided `assignment.ipynb` iPython notebook while backing up your work with git and running local tests.
 - Submit your work to a server, which will run a private set of tests to grade your submission.

By using this workflow, you will:
 - Gain exposure to `git`, the most popular tool to track changes, backup work, and collaborate with others.
 - Become familiar with using iPython notebooks, a common tool for interactively working with Python.
 - Develop strong software engineer habits like testing code, maintaining consistent style, and using source control.

At this point in your CSE education/curriculum, you may be familiar with all or some of these concepts
(and thus you can skip over some parts).
It is up to you to make sure that you have the knowledge and tools to complete these labs.
TAs may be available to help you with some questions and issues,
but this document, common-sense research, and your past experience should be sufficient to complete the procedural components of these labs.

## Preparation

First, we will cover the tools we recommend you use in this course.
If you prefer other tools you may use them,
but the TAs may not be able to help you if you encounter difficulties.

### Supported Setups

Below are the supported setups for this course.
This means that these setups are the ones that the course assistants will be able to help you with.
Other setups can work, but the course assistants are not required to help debug those setups.
See respective sections "Command Line" and "Python" for more detailed information.

Python 3.10 or 3.11 is required for this course.
Instructions on how to install Python can be found [here](https://wiki.python.org/moin/BeginnersGuide/Download).
We also recommend you to use [pip](https://en.wikipedia.org/wiki/Pip_(package_manager)) to install Python packages.

For [Linux](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)
and [Mac](https://support.apple.com/guide/terminal/execute-commands-and-run-tools-apdb66b5242-0d18-49fc-9c47-a2498b7c91d5/mac),
we recommend using the built-in command lines interfaces, see the links for further information.

For Windows, we recommend using [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/).
Note that this is different than the built-in cmd.exe or PowerShell.

### Command Line

Throughout this course, we will be giving you directions on how to perform various tasks.
The easiest way for us to communicate those instructions and most universally applicable way to do this is by using a command line.
Different command line interfaces are available on all operating systems, and we will go over some recommendations below.
For this class, we specifically recommend POSIX-style command lines which excludes Window's CMD and Powershell.

For Linux and Mac, command line interfaces (e.g. terminals) are available without additional steps.
Guides on getting started can be found [here for Linux](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)
and [here for Mac](https://support.apple.com/guide/terminal/execute-commands-and-run-tools-apdb66b5242-0d18-49fc-9c47-a2498b7c91d5/mac)
(as well as all over the internet).

For Windows, we recommend you use Windows Subsystem for Linux (WSL).
WSL is natively built into Windows and is available for free, but requires some additional steps [described here](https://learn.microsoft.com/en-us/windows/wsl/).
The setup for WSL is dependent on your version of Windows and your machine settings,
so make sure to consult the [FAQ](https://learn.microsoft.com/en-us/windows/wsl/faq)
or [troubleshooting guide](https://learn.microsoft.com/en-us/windows/wsl/troubleshooting) if you are having issues getting WSL working.

### Python

We will be using Python (versions 3.10 or 3.11) in this course.
(Most other version >= 3.8 are likely to work, but not officially supported.)
If you don't already have Python installed,
instructions for your OS can be found [here](https://wiki.python.org/moin/BeginnersGuide/Download).
If you are new to Python environments,
We recommend that you try to only have one version of Python installed on your machine at a time
(it is possible to have multiple version, but that can get pretty confusing).

To check your already installed Python version, use:
```sh
python3 -V
```

If you want a refresher on Python, we recommend one of the following resources:
 - [Text Tutorial](https://overiq.com/python-101/)
 - [Video Tutorial](https://www.youtube.com/watch?v=eWRfhZUzrAc)

Note that we will typically use the `python3` command.
Because of the breaking changes between Python 2 and 3,
when you install Python on your machine an additional executable called `python2` or `python3`
(depending on the version of Python you installed)
will also be installed on your machine.
Since this course only uses Python 3,
any use of the `python` command refers to `python3`.
This also applies to the `pip` and `pip3` commands.

### Virtual Environments and Python Packages

In Python, code that is not your own or apart of the [Python standard library](https://docs.python.org/3/library/index.html)
is considered a third-party package (sometimes just shortened to "Python packages" or just "packages").
Each package can be associated with different versions and require specific versions of other packages as dependencies.
Since it can be hard (or maybe even impossible) to get a set of packages that satisfy the versions of every package needed,
we use a tool called [virtual environments](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment), or "venvs" for short.
Virtual environments lets you create as many environments as you want and install a different set of packages (or package versions) to each venv (you can even use different versions of Python).
For example, maybe you are working on this class which uses a new version of the pandas package,
but you are also maintaining an old piece of code you wrote 5 years ago that uses an older version of pandas.
You can just create a venv for each project and have both versions of pandas installed on your machine at the same time.

In this course, we will be using the [standard venv tool](https://docs.python.org/3/library/venv.html) distributed with Python.
(You can use others, but the TAs cannot officially help you with them.)
[This guide](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment)
covers how to create an use venvs,
we will reiterate the steps here.
(For Windows, some of the commands are different from the ones listed here, but the general steps are the same.
Refer to the linked guide for the exact commands.)
Before using a venv, you must create it:
```sh
python3 -m venv cse146_venv
```
(In this document, we will assume that your venv is called `cse146_venv` and it is located in the same directory you are running commands in.)
Once created, a venv will be a normal directory that holds all of its information and packages,
so you can create it anywhere you like on your machine.
To use your newly created venv, you will need to [activate](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#activating-a-virtual-environment) it:
```sh
source cse146_venv/bin/activate
```
Now you may notice that your shell prompt has changed, this is a sign that the venv is working.
With your venv activated, any packages you install will automatically be installed to the venv,
and any packages used/imported will come from the venv.
If you want to stop using the venv, you can just deactivate it at any time:
```sh
deactivate
```
Note that your shell prompt should have changed back.
Your venv can be re-activated at any time in the same way as before.

Now that we have our virtual environment sorted out, we need to install the packages for this course.
We defined all the dependencies in this course using the [standard `requirements.txt` file](https://pip.pypa.io/en/stable/reference/requirements-file-format/).
You will find this file in the same directory as this readme.
You can install all the course requirements at the same time using this file.

In this course we recommend you use [pip](https://pip.pypa.io/en/stable/) to install packages.
You are free to choose whatever system works best for you (like [Conda](https://docs.conda.io/en/latest/)),
but the TAs may not be able to help you if you are using a different setup.
Make sure you have activated your venv before running any pip commands.
To install the requirements in `requirements.txt` with pip, you can use:
```sh
pip3 install -r requirements.txt
```

For each assignment, you may use the Python standard library and any packages specified in `requirements.txt`.
Unless specified, you are to use no other packages.
Use of other packages in assignments may be considered cheating.

### Jupyter Lab

In this course most your assignments will be distributed in the form of iPython notebooks,
and we encourage you to work with them through [Jupyter Lab](https://jupyter.org/).
iPython notebooks, "notebooks" for short, let you write Python code in an interactive environment that
can display visual elements like images and graphs.

Unfortunately, notebooks are not intended to be edited directly like most source code files.
So, we will be using Jupyter Lab to work with our notebooks.
When we run Jupyter Lab, it will open a session in a web browser that allows us to edit and view our notebooks.

For a tutorial on iPython notebooks with Jupyter Lab, see:
 - [Text Tutorial](https://www.dataquest.io/blog/jupyter-notebook-tutorial/)
 - [Video Tutorial](https://www.youtube.com/watch?v=HW29067qVWk)

### Git

Source control lets you keep track of different versions of your code,
back it up to remote servers,
and easily share it with people you are working with.
Although you will generally be doing this course's assignments alone,
you will still be using source control to keep track of the changes to your own code and to back it up.
Additionally, we will be distributing your assignments to you via source control.

In this course, we will be using [Git](https://git-scm.com/) for source control.
Git is by far the most popular source control system, with over 96% of
[professional developers preferring Git](https://survey.stackoverflow.co/2022/#version-control-version-control-system).

For hosting our Git repositories, we will be using [GitHub](https://github.com/).
It is free to use and allows you to make unlimited private repositories.
Make sure to sign up if you don't already have an account.

If you want a primer in Git, we recommend one of the following resources:
 - [Text Tutorial](https://nulab.com/learn/software-development/git-tutorial/git-basics/)
 - [Video Tutorial](https://www.youtube.com/watch?v=RGOj5yH7evk)
 - [Official Online Book](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

#### SSH Keys

When using git, the easiest way to authenticate (login) from the command-line is to use [SSH keys](https://wiki.archlinux.org/title/SSH_keys).
SSH keys are a pair of keys (a private key and a public key) that you can generate to let other people/programs/servers know who you are.
You want to make sure to always keep your private key **private** and never give it to anyone else.
You can share your public key with anyone who wants to authenticate you (like Github).
Github essentially requires that you use SSH keys when working with private repositories
(you can technically use [Personal Access Tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-personal-access-token-classic),
but those are not recommended for this course).

By default, SSH keys live in your `~/.ssh` directory (where `~` means your [home directory](https://en.wikipedia.org/wiki/Home_directory).
You can look in there for any existing SSH keys that you have (and skip the next step if you want).
By default, keys start with the `id_` prefix.
Public keys will have the `.pub` suffix, while private keys will have no suffix.

To generate SSH keys, we use the `ssh-keygen` command.
There are various options that you can use to change the security on the key generated,
but the default settings are good enough for this class.
`ssh-keygen` will ask you two questions:
 - Where you want the new key to be placed.
   - If this is your first key, then the default location is fine.
     If this is not your first key, then you should choose some other name that you can remember (in this example, we will use `id_github`).
 - If you want to use a password for your key.
   - This is an additional level of security that you can have, so that every time you use the key it asks for a password.
     A good rule of thumb is that if you are using a machine that is secure and only you use, then you don't need a password.

Here is an example of running `ssh-keygen`:
```
eriq@horsea:~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/eriq/.ssh/id_rsa): /home/eriq/.ssh/id_github
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/eriq/.ssh/id_github
Your public key has been saved in /home/eriq/.ssh/id_github.pub
The key fingerprint is:
SHA256:FXYWHE2Iu8e7SjSzqwexdKC8EV/4kpdrYM1mkofm4NU eriq@horsea
The key's randomart image is:
+---[RSA 3072]----+
|         .oo=*.  |
|      . o.o+o .  |
|     . + @.o     |
|      = #.E      |
|     . XS%++     |
|      o +.++o    |
|         oo. .   |
|         ....    |
|        .oo...   |
+----[SHA256]-----+
eriq@horsea:~$
```

Note that `ssh-keygen` now created the public and private keys in my `~/.ssh` directory:
```
eriq@horsea:~$ ls -lh ~/.ssh/id_github*
-rw------- 1 eriq eriq 2.6K Oct  2 13:43 /home/eriq/.ssh/id_github
-rw-r----- 1 eriq eriq  565 Oct  2 13:43 /home/eriq/.ssh/id_github.pub
eriq@horsea:~$
```

Now that you have your keys (whether you just generated them or you already have them),
you need to give Github a copy of your **public** key.
So, copy the contents of your `.pub` file.
(If you don't have a fancy way to directly copy a file into your clipboard,
then you can just `cat` the file and use your mouse to copy it).
In our example, we would do:
```
eriq@horsea:~$ cat ~/.ssh/id_github.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDeRxnqHb/XPJ3PhO6Ez5QPNdse1ANoMgQPkjN1+bp50hBrfLwB5lI6SQwvmn6zMr+NwpEg9UjVmniINN9qqehgSVugzQbr0jZz22qssWRuxeE8JFrpaqt0jYjItGJUynmDpuBYeC9Rv05gjg8cGKoBhLbjfFeftRk/pc03MfpfSUCNNMMABtOzfnKnerteGg15YAZ2y58KKNEmAjYRCM3khTcSxVzhL/TfHdO6xky2921Zg190GQtZv/EQIHeQMQG63cI23fd+Bm3p+H8I/WFdLYvTX9eTIxfbdX6wGAgx3FjuKdiamkKDaDniJQMwswXnyEcJ17Y+MYVvFX/8Pq/wbnCj3PWIGLJ9Fx57ORK++wTj7K3uQ33lA0EpjYZjMZXVXFIVHwre9D0XPgbLwb5+26JAxRu1o+mnrqGb/a8fFUO0JyPpuiAWvGiaGSty21sZ1TVPwqJ3N9A0vmxASgLcyfl7AmhIwdwI9DMxyyYQ62HYJJ+EnT9MPQvYv+/WG4U= eriq@horsea
eriq@horsea:~$
```
Note that they keys typically start with `ssh-` and end with a name or email.

Now go into the "SSH and GPG keys" section of your Github settings: https://github.com/settings/keys .
Click the green "New SSH key" button.
Give your key a name and paste the contents of your key into the "Key" section.
Click the "Add SSH key" button and you should be all set!
Now you can use Github in the terminal without needing a password.

If you have a non-standard setup, then there are more complete (but more complicated) instructions all over the internet:
 - [Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
 - [ArchLinux Wiki](https://wiki.archlinux.org/title/SSH_keys) (good for general Linux setups)
 - [MacWorld](https://www.macworld.com/article/671164/how-to-generate-ssh-keys.html)
 - [GitLab](https://docs.gitlab.com/ee/user/ssh.html)
 - [WSL (Ubuntu)](https://ubuntu.com/tutorials/ssh-keygen-on-windows#1-overview)

### Additional Resources

We anticipate that students in this course will have a variety of preparation and prior exposure to tools such as
the command-line, powerful text-editors (such as vim), version control software (such as git), etc.
While we have included links to resources and documentation for some of the tools we expect you to use in this course,
a more comprehensive introductory source is provided by MIT under the course title
["The Missing Semester of your CS Education"](https://missing.csail.mit.edu/).

While this material is not required,
setting up and learning to use proper tools can save you hundreds of hours of work over the course of your undergraduate education,
and having experience with these tools will serve you well in the job market.
Even experienced students are likely to benefit from the linked content!

## Assignment Workflow

0. **Verify GitHub Access**

    First, ensure that you have your GitHub authentication setup so you can work with your own private repositories.
    We recommend using [SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh), since they are widely used, secure, and convenient.
    Generating and using SSH keys was covered in a previous section.
    However if you can't use SSH keys for some reason, then [Personal Access Tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-personal-access-token-classic) are also an option.

    Our instructions will always assume you are using ssh keys.
    If you don't then the commands should be the same, but repository URLs will be different (and you may be asked for a password).

1. **Create a Private Repository Using Our Template**

    The assignment repository that we provide is a GitHub template,
    so you can create your own private repository from it.

    Starting from the [assignments' GitHub page](https://github.com/ucsc-cse146/cse146-labs), click on "Use this template" -> "Create a new repository".

    Give this repository a name and an optional description,
    and **make sure your repository is private (the "private" option is selected).**
    Sharing code outside of your group (even if unintentional) may result in a violation of academic integrity.

    Now click "Create repository from template" to create your own private version of the assignment repository.

    Once you have your repo, you can share it with any collaborators "Settings" -> "Collaborators and teams" options.

2. **Clone Your Repository**

    Clone your newly created private repository.
    (If you are new to git, "cloning" a repository is when you make a local copy of the repository on your machine.)

    ```sh
    git clone git@github.com:<username>/<repo name>.git
    ```

    For example, Sammy Slug (sslug) would clone like:
    ```sh
    git clone git@github.com:sslug/cse146-labs.git
    ```

    Now move into the newly created directory:
    ```sh
    cd cse146-labs
    ```

    You may verify the contents of this new "local" repository by running
    ```sh
    ls
    ```

    This should list the following files inside your repository
    (without the comments ("#")).
    ```
    README.md           # The file you are reading now!
    lab1
    lab2
    lab3
    requirements.txt    # The file defining the Python requirements for the labs.
    ```

3. **Edit config.json**

    Every lab comes with a `config.json` file the tells the autograder about you and your submission.
    You can edit this file to contain your own specific information.
    (You can also delete/bypass/ignore this file completely [if you want](https://github.com/edulinq/autograder-py?tab=readme-ov-file#configuration).)

    Open up `config.json` and put your information in there:
     - `course` -- The current course you are enrolled in (already set).
     - `assignment` -- The current assignment you are working on (already set).
     - `server` -- The autograding server to submit assignment to (already set).
     - `user` -- Your username (email) for the autograder.
     - `pass` -- The password that was emailed to you in the beginning of this course.
                     If you didn't get the password, forgot it, etc; talk to a TA.

    For example, Sammy Slug would have a `config.json` for LAB1 that looks like:
    ```json
    {
        "course": "CSE146",
        "assignment": "LAB1",
        "server": "http://lighthouse.soe.ucsc.edu",
        "user": "sslug@ucsc.edu",
        "pass": "1234567890"
    }
    ```

4. **Save Your Changes in Git**

    Now would be a good time to save your changes in git.
    In general, you want to save your changes anytime you
    finish implementing a feature (something new that your code does)
    or fix a bug.
    However, if you are new to coding it can be hard to decide when is the best time to save your code.
    So our general advice is err on the side of caution and save more often,
    and especially make sure to save when you leave your computer.

    "Saving" with git is a two-step process: commit and push.

    The first step is to "commit" your changes,
    this bundles up all the changes you have done since your last commit and adds it to your repo's history.

    First check the status of your repository:
    ```sh
    git status
    ```

    You should see something like:
    ```
    On branch master
    Your branch is up to date with 'origin/master'.

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   config.json

    no changes added to commit (use "git add" and/or "git commit -a")
    ```

    You can also see all your exact changes with a diff:
    ```sh
    git diff
    ```

    Which will show something like:
    ```
    diff --git a/config.json b/config.json
    index 13f4424..5ac423f 100644
    --- a/config.json
    +++ b/config.json
    @@ -1,4 +1,4 @@
    {
    -    "user": "sslug",
    -    "pass": "1234567890",
    +    "user": "cse146TA",
    +    "pass": "TAsAreCool",
    }
    ```
    Where lines that start with a "-" are the old code and lines that start with a "+" are your new code.

    Now, we can add the files we want to include in this commit with `git add`.
    (If git has already included this file before and you are just making changes,
    you can also use `git commit -a` and skip the `git add` step.)
    ```sh
    git add config.json
    ```

    Now `git status` will show the file ready to be committed:
    ```
    On branch master
    Your branch is up to date with 'origin/master'.

    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        modified:   config.json
    ```

    Finally, you can commit your changes with `git commit`.
    Make sure to always include a commit message with the "-m" argument so you know what you did in this commit:
    ```sh
    git commit -m "Added my credentials to the config.json file."
    ```

    The next part of "saving" your changes with git is to send your changes to GitHub
    (or wherever you are saving your code).
    This is done using a `git push`.
    If you are working with others make sure to get new changes (`git pull` before pushing),
    but otherwise pushing is very simple.

    Do a `git status`, and git will show you that your repo has newer commits than GitHub:
    ```
    On branch master
    Your branch is ahead of 'origin/master' by 1 commit.
    (use "git push" to publish your local commits)

    nothing to commit, working tree clean
    ```
    In this output "origin/master" refers to GitHub, and git says that our local copy is 1 commit ahead of GitHub's version.

    Now we can just push:
    ```sh
    git push
    ```

    Now you should be able to see your local changes online in GitHub.

5. **Work on the Assignment**

    Make sure your venv is activated.

    Now, you can start Jupyter Lab and start your assignment!
    ```sh
    jupyter lab
    ```
    This should open up Jupyter Lab in a web browser.
    If not, directions should be printed in the terminal.  

    If you are having trouble launching Jupyter Lab,
    consult their [installation documentation](https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html#pip).
    

    If you are getting an error like "bash: jupyter: command not found",
    and running the following fixed it (as per the documentation):
    ```sh
    export PATH="$HOME/.local/bin:$PATH"
    ```
    Then you can put the above in your `~/.bashrc` and you won't have to repeat the comment every time you want to launch Jupyter.

    With Jupyter Lab open in the browser, you can work on your assignment:
     - Open `assignment.ipynb` as listed on the left side of the page.
     - Read the instructions for the assignment, and complete the required task(s).
     - **Make sure to save your work by clicking on the `save` button in the interface!**
    This should be done before testing or submitting.

6. **Test Your Assignment**

    All assignments include a `local_grader.py` script that allows you to see how your code is performing so far.
    It will grade you in the same way that the autograder will grade you and give you similar output.

    **Note that the score your get from the local tests is NOT official.**

    In the command line, you can run the local tests with:
    ```sh
    python3 ./local_grader.py assignment.ipynb
    ```

    If all goes well, you should see something like the following:
    ```
    Autograder transcript for project: Practice Grading for Lab 1.
    Grading started at <omitted> and ended at <omitted>.
    Question Q0: 100 / 100
    Question Style: 0 / 0
        Style is clean!

    Total: 100 / 100
    ```

    If not, you will instead see something like the following:
    ```
    Autograder transcript for project: Practice Grading for Lab 1.
    Grading started at <omitted> and ended at <omitted>.
    Question Q0: 0 / 100
        Function must return a boolean value.
    Question Style: 0 / 0
        Style is clean!

    Total: 0 / 100
    ```

    We encourage you to expand your copy of `local_grader.py` with your own tests.

    In general, you should develop the habit of frequently running the local tests.
    You have little chance of getting a good score with the real grader if you cannot pass the local tests.
    In particular, you should not spam submissions in lieu of testing!

7. **Submit Your Assignment**

    Once you have passed the local tests and are ready to submit,
    you can do so using the command:
    ```sh
    python3 -m autograder.cli.submission.submit assignment.ipynb
    ```

    This will take your `config.json` and `assignment.ipynb` from your current directory
    and send them to the autograding server.
    The autograder will get your code and run a bunch of secret tests on it to assign you a grade.
    It will return output formatted about the same as the local tests.

    The autograder records all your submissions (the code, time, and score).
    The score you received on your most recent submission is your current grade for the assignment
    (not counting late assignments and manually graded components).

    You can make as many attempts as you want.
    However if we find you abusing the autograder (e.g. repeatedly failing tests that would have been caught by testing locally),
    then you can lose points.
    Any attempt to willingly circumvent the autograder (e.g. "hacking" it)
    may result in an immediate F in this class and a referral for academic integrity.
>>>>>>> template/main
