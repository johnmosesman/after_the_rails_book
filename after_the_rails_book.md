# Extra topics

This is a list of topics you should be familiar with that may or may not have been covered in the Rails book.

## How to use this doc

* Fork this document on Github
* Answer/complete the sections below and commit your changes to your forked version of this doc.
* Start by editing the space below to include your name and date (note: you may need to review [Markdown syntax](https://daringfireball.net/projects/markdown/syntax) first)

```
your-name-and-date-here
```

* Next, create a new branch called `name-and-date`, commit your change, push it to Github, and create a pull request (PR).
* Review the pull request and merge it.
* Continue with that process for the remaining sections (you don't have to do a PR every time, you can merge from the command line if you want).


The sections below can be done in any order, so feel free to skip around if you get stuck.


## Build a personal blog

Every developer needs a personal blog/site. Blogs are a great resource for other developers, and you'd be surprised what you know that someone else is trying to figure out—no matter how simple it seems. The best way I've heard it put is, "Write to yourself from 6 months ago about what you wish you knew then."

Blogs are also social proof that you know some things. Most of the time, blogs are built using what are called "static site generators." The idea is that for a blog that justs loads static HTML pages, you don't need a full-fledge app with a database, routing, controllers, etc. Just a static website is good enough. So:

* Build a static site using [Jekyll](https://jekyllrb.com/) with a "hello world" post (add real posts too if you want to).
* Deploy it to GitHub pages. 
* (BONUS) Setup a custom root and sub domain to point to that site (i.e., "johnmosesman.com" and "www.johnmosesman.com").
* Put the link to your site below

```
your-sweet-site.com
```

## APIs

### What is an API?

```
your answer
```

### What status codes are _usually_ returned for the following responses, and what do they mean?

- Success: ` `
- Created: ` `
- Unauthorized: ` `
- Unprocessable entity: ` `
- Not Found: ` `
- Internal Server Error: ` `

### What are the most common HTTP verbs sent with a HTTP request, and what CRUD actions do they map to?

```
your answer
```

### Build a Rails API that returns JSON for standard CRUD actions on a "user" object.

This is probably the largest task in this list, but APIs are everywhere. Take your time and go step-by-step.

- (Maybe) look up what JSON is
- Create a rails app using the `--api` flag
- Put it under the `/api` namespace
- Write tests for every endpoint
- Use [cURL](https://curl.haxx.se/) to hit each API endpoint (show the request you made and the responses for each)

```
your curl requests and responses
```

After you've completed the above, put the "update" and "delete" endpoints behind token authentication. To do this:

* Assign each user a secure, randomly-generated token
* In the HTTP request, pass the token via the "Authorization" header.
* Parse the HTTP header and try to look up the user that matches the token. Based on the result, either return unauthorized (see status codes above) or allow the action to go through.

```
the authenticated curl requests and responses
```

## CSS frameworks (Bootstrap/Foundation)

Most companies use a CSS framework to give them easy page layouts and mobile responsive sites. You should be familiar with the concepts of the two leading frameworks: [Bootstrap](http://getbootstrap.com/) and [Foundation](https://foundation.zurb.com/).

1. Create a simple HTML page (doesn't have to be a Rails app) with two rows and a 4-3-2-up grid for large-medium-small screens respectively
2. Do this by including the Bootstrap framework files directly into the `<head>` or `<footer>` elements.
3. Add a README.md file with a description and a screenshot of the page
4. Push it up to Github and put the link below.

Next, do the same thing but use the ruby gem for Bootstrap instead of including it directly.

Finally, do the same thing as above but using Foundation. Put the Github links below.

```
link-to-bootstrap-page
link-to-bootstrap-rails-app
link-to-foundation-page
link-to-foundation-rails-app
```

## jQuery

"Modern JS" has evolved past jQuery and will scoff at this, but jQuery is still used in a lot of places, and the concept of events and triggers is something you should at least be familiar with.

1. Include jQuery in an HTML page (doesn't have to be a Rails app)
2. Using vanilla HTML/CSS, create a simple page that has two paragraphs—one visible and one hidden.
3. Add a button with text "Toggle" to the page, and using jQuery, when the button is pressed toggle the visible paragraph to be hidden, and the hidden to be visible.
4. Next, add another button with text "Hover" that toggles the paragraphs only while your cursor is hovering over the button.

## Command line stuff

### vim 

I have this section only as a way to get familiar with basic vim commands, as they are often used in conjunction with editing git commits. At some point you will want to consider switching to a more powerful text editor than sublime/atom/etc., but those are perfectly fine for now.

1. At the command line, type `vimtutor` and follow its instructions. This should take ~30min.

## git / bash

### Tutorial

Git can do a lot of things, and it's not always super obvious. I would recommend reading through [this tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository) with the aim of trying to learn what you can, and not worrying about 100% mastery yet.

### Some practice

Using the command line only:

1. Create a new folder somewhere on your machine
2. Change into the folder and initialize git
3. (Try to use the command line for this) Create a text file and open it in your editor (or vim!!)
4. Write something in there and commit the change with a message.
5. Create a repo on Github and push up the file.

Next:

6. Write something else and commit again locally with another message.
7. Amend your previous commit message and put `(AMENDED)` at the end of the message.
8. Run `git reset --hard origin/master`. Oh no your last change is gone!
9. Use `git reflog` to recover your change.

Save your commands and paste them below.

```
$ your commands here
```

## dotfiles

Dotfiles are configuration files for programs you use on the command line. By convention most of them end in "rc" (`.bashrc`, `.vimrc`, `.railsrc`) and the file name starts with a dot (which means "hidden" file).

Dotfiles are very powerful and do a lot of things, but for now let's use two simple use cases.

### aliases

You're going to type certain commands _over and over and over and over_. Things like `rails db:migrate`, `git status`, and `bundle install`. Eventually you will get tired of typing these things, and you will want a faster way—enter aliases.

If you're on Mac OSX, you're probably using `bash` as your default command line shell. Bash has a configuration file named `.bashrc`. This file might already exist in your home directory on your machine. Run the following to check: 

```
$ ls -a ~/ | grep bashrc
```

That command lists all files in your home directory (`~/`) and passes the output (via the pipe operator `|`) to the `grep` command, which searches for the text `bashrc`. The `-a` flag means include "hidden" files—or these whose file names start with a dot (like our `.bashrc` does).

If you see the `.bashrc` file as a result that's great. If not, make the file like this:

```
$ cd    # `cd` with no arguments is a shortcut to the home directory
$ touch .bashrc
```

Run the search command again. You should see the new file there now.

Open up `.bashrc` and add the following lines:

```
alias bi="bundle install"
alias gs="git status"
```

Save the file, and run the `source` command to reload the configuration file in your shell: `$ source ~/.bashrc`.

Now switch to a directory that has a git repo initialized and type `gs`. You should see the result of `git status` printed out.

I've made aliases for _tons_ of commands. There are some commands that I can't seem to type correctly, so I just alias my most common misspellings to the actual command. For example: `alias rbnev="rbenv"`

### Configuration

Dotfiles aren't just for aliases, they're intended for configuration. Create a new file in your home directory called `.railsrc`, and put the following:

```
-B # Skip bundle
-d postgresql
```

Source the file, and the next time you create a new rails project it will skip bundling at the start, and default your database to Postgres instead of sqlite.


## SQL

TODO