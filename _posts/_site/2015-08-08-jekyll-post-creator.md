Welcome to re-launch of my blog. I hope this time I will do better job and find motivation and enough time to create new content more frequently.
For new launch I decided to try out Jekyll. Why? Mostly because of its simplicyty and trying to save some time for actually creating content.
The way Jekyll is handling post creation is by placing files in _posts folder. Each file has common name template. It starts with date followed by title. Each word is separated by minus sign.
Quick example for today's post will be 2015-08-08-automate-creation-of-Jekyll-blog-posts.

Why do I want to automate such a easy task? Simply, because why should I remember about that format? Why should I get annoyed and type - characters after each word. And there is opportunity to practice some new technologies I feel rusty like shell scripting.

The way I imagine this to work is simple shell script taking title as a parameter (title) and creating file in correct location. For now I will hardcode location of project to skip passing another param. I will leave it to you as a homework :)

Here is the code. Hope someone will find it helpfull.

#!/bin/bash
PROJECT_DIR=/Users/lukasz/dev/izmajlowiczl.github.io/_posts
touch $PROJECT_DIR/$(date +%F)-$(echo $@ | tr ' ' '-').md
