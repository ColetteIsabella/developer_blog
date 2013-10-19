---
layout: post
title: "Octopress for Hackers-To-Be 1.0"
date: 2013-09-20 16:34
comments: false
categories: Jekyll, blogging, Octopress
---

# Let's Create an Octopress Blog!


#### * $ means that you are entering a command into console.

Two months ago, I had no idea what a console was, what my husband or my father were talking about, when they told me about their work, commands and structures and Agile and... My dad's a Java Engineer, and my husband is a UX Designer.
I started playing with <a href= http://www.codecademy.com/>Code Academy</a> Then I realized, this is how I think! Even better, I found <a href= https://www.codefellows.org/>Code Fellows</a>, in Seattle. I took their bootcamp on Ruby on Rails, and boom, life => changed.
But that's not why you're here, you want to know how/why/what you're reading. Maybe you're curious about starting your own all-you designed blog, maybe you've heard of <a href= http://octopress.org/>Octopress</a>, either way, this is how a noob with a Ruby understanding, made this:
First off, I cannot emphasize enough the importance of Reading Everything. If you have even a marginal understanding of code, and you try running at this with just that, a lot of complications will slap you in the face.
I also recommend the IRC channel #octopress, for anything you get stuck on. But let's try to avoid complications. With all luck, you won't run into any problems, but since I did, I will show you mine, and you can skip the ones you don't have and ask about ones I didn't run into. (A substantial amount of coding, is messing up)
###I'm assuming you have git, Ruby, and RVM or RBENV installed. And you need to use ruby version 1.9.3 for now, check it with
$ ruby --version
So let's get statrted.

###The install process:
Following the directions from the page, it recommends a clone. This is what I used, and it was quite clean, but forking their repository is also a valid method, here are the differences:

If you choose to clone, you will cd into your Dev directory (you should have a designated Dev directory to reduce confusion.)Copy this in to that directory:
+ git clone git://github.com/imathis/octopress.git octopress>
Then you need to switch into the octopress directory using:
+ $ cd octopress
The documentation recomends you check your Ruby version here, just know that if you are not in 1.9.3, you might not get the results you want.
Next, you'll type
+ $ gem install bundler
If you are using rbenv, you'll want to run
+ $ rbenv rehash
Then $ bundle install
+ $ rake install
This is where it gets fun, and this is where we need to stay calm. There are a few ways this can go: it could show up brilliantly with the deafult interface saying- Your Octopress Blog, Or, it could be sparce and look a lot like html with no CSS structure.
Either way, let's start with our new favorite file: \_config.yml. It looks like this(with examples):
+ url: your_website.com
+ title: The Cheese Blog
+ subtitle: Cheese should not be orange, or bounce
+ author: Richard Ayoade
Below that:
+ root: / <= it should be that unless you have a special, different route.
+ permalinks: (leave this alone unless you know what you're doing)
+ source: source
destination: public/ <= It might automagically add your github repo, don't keep it. it's a trap!
Now some decisions come up, I chose<a href=http://octopress.org/docs/deploying/github/> Github Pages</a>, it's easy, and I'm used to it. But that didn't make it simple.

There are other particulars to watch out for with Heroku and Rsync, but since I didn't use them, I'll go through gh-pages.
First off, you want to create a Github Repository, if you cloned in, it should be set up, but launch GitHub and check to make sure your initial commit was successful.

Then, you use the rake configuration to get your pages set up:
+ $ rake setup_github_pages

Easy peasy, right? It asks for your Repo url, and then should do some other things...Well you'll want to check those went through before you go all gung ho on this.
Make sure that your new origin was created by typing:
$ git remote -v You should see:
+ octopress git://github.com/imathis/octopress.git (fetch)
+ octopress git://github.com/imathis/octopress.git (push)
+ origin git://github.com/your/repo.git (fetch)
+ origin git://github.com/your/repo.git (pull)
If you only see the first 2, DON'T PANIC, you just need:
+ $ git remote add origin git@github.com:username/username.github.com.git

Now you need to create a source directory in your repo to work from **Wait! What happened to Github Pages?!?** Believe me, this will go a lot smoother if you set all this up now.
+ $ git branch
Should say: master
+ $ git branch -m master source
+ $ git branch
Should say: source. Hooray! This set up your _deploy branch, which will become near and dear.
If you have a custom domain you want to run your site on, it's an awkward, but doable set of steps.
First, register your Domain with whoever. Seriously, whoever.

#### Note, I just heard an interview with Richard Ayoade, where he talked about cheese, apologies, it's just on my mind.

Once you have whitecheeseforever.org, you'll want to go into the DNS settings on your chosen page. DNS means Domain Name System, so even though it sounds like a scary techy term, it's quite asinine.
Here's what you want to change:
whitecheeseforever.org  - A - 204.232.175.78
(Different sites give different numbers, but this is the one which I see most often, and which seems to work for me.)
If you want it to redirect from www.whitecheeseforever.org, you will also want:
www.whitecheeseforever.org -CNAME- username.github.io<
This will take a while to kick in, so don't get too excited, instead, go back to your console and type:
+ $ echo "whitecheeseforever.org" >> source/CNAME

####Okay, yeah, the cheese thing got a little old on me too...

Hooray! There's now a new file called CNAME in your source folder. Go make sure there is only ONE domain name in there. Just the one with no www. Go ahead, I'll wait. Just one? Then onwards to greatness!
Now back to console, and hit:
+ $ rake generate
+ $ rake deploy
And you're running! Tomorrow, we'll write our first blog post, check our themes, bug check, wonder why it doesn't work, wonder why it works, then show the world our Hacker skillz!
For now, you need to wait for your DNS to catch up, and I need to feed my impatient cats, who will never understand why I use their warm bed to click all day.
Until tomorrow!




