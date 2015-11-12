Welcome to re-launch of my blog. 
===============================
I hope this time I will do better job and find motivation and enough time to create new content more frequently.

For new launch I decided to try out Jekyll. Why? Mostly because of its simplicyty.
The way Jekyll is handling post creation is by placing files in *_posts* folder.
Each file has common name template. It starts with date followed by title. Each word is separated by minus sign.
Quick example for today's post will be *2015-08-08-automate-creation-of-Jekyll-blog-post-files.md*

### Why to automate such an easy task?
* I'm really bad in repeating tasks. Let's leave it to computers.
* I don't need to remeber format of file
* There is an opportunity to practice some new technologies.

The way I imagine this to work is simple shell script taking title as a parameter (title) which createsfile in correct location. 
For now I will hardcode location of project to skip passing another argument. I will leave it to you as a homework :)
To use it, just run script with your title like ```./new_post.sh Automate creation of Jekyll blog post files.```
(You need to add executable permissions chmod +x to file)

<code>
\#!/bin/bash <br /><br />
PROJECT_DIR=~/izmajlowiczl.github.io/_posts <br />
touch $PROJECT_DIR/$(date +%F)-$(echo $@ | tr ' ' '-').md <br />
</code>

Those two lines of code may really sound trivial. Nevertheless for me it was fun to spend few minutes playing with shell and especially figuring out what is wrong with:  
`PROJECT = ~/izmajlowiczl.github.io/_posts/`.<br /><i>* Tip: When declaring variables in BASH script do NEVER surround = with spaces</i>

Hope someone will find it helpfull. For now that't it!
