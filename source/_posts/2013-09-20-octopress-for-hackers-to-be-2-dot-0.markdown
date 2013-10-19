---
layout: post
title: "Octopress For Hackers-To-Be 2.0"
date: 2013-09-20 16:35
comments: false
categories: Jekyll Octopress,
---

# Let's Create an Octopress Blog! Part 2 #


#### * $ means that you are entering a command into console. ####
As we left off last time, we had set up our DNS (Let's check that real quick):
$ dig yourwebsite.com +nostats +nocomments +nocmd
This should return your "global options", and you should see listed your CNAME set up, if you did that, and yourwebsite.com  A  204.232.175.78</p>
### If this is not what you see, ###
or there are more numbers than the 204 Record, you'll need to go back to you DNS server, and

1. Make sure it has the right number, and it's entered correctly.

2. Make sure it's not trying to do anything else, like host your site in its own system, you don't need nameservers, and if it has a space where you can tell it you are using GitHub Pages, that is ideal.


Let's meet our first new best friend:

\_config.yml, where you will find:

+ url: http://example.com
+ title: The Title of your new Fancy Site!
+ subtitle: Explain why I care
+ author: Your Name, this is key as this is a reference file, and your pages and posts will look here to enter the right fields

+ --Somethings you may or may not care about--

+ root: /  <= Unless you want it going somewhere else, this is what you want to tell it
+ Some more blah blah, we'll play with these later, maybe
+ GitHub user: YourName <= There is an autofill written to fill out the link for these, so you want to just put your GH name.
+ Same for LinkedIn and Twitter if you want to use them, just your name for those sites will do, or it will misdirect.

Now let's go see if our basic, classic theme is working. First, we need to submit our changes.(Remember you should be in git source)

$ git add .
$ git commit -m "Updated \_config file"
$ git push
$ rake generate
$ rake deploy

Load up your website, and see what you see, it should be a very basic layout, but Most important, is you should see something other than just the default "Your Octopress Blog", if that is what you see, you'll need to make sure that all your changes are tracking to GitHub. Make sure you have a Master, Source and gh-pages option, if not, we've got some debugging to do. I have put this together after actual days of searching for all of the little fiddly bits. Quicker, head over to the #octopress irc channel, but this is all fixable.
DO NOT PANIC and erase your file on GitHub and your computer. Believe me, it just gets messier.
So we've got the basic layout, one way or another, we got here, now let's pretty it up.
You have a few options here, if you do as I recommend, which is Read Everything, you can figure out your own color customizations in the .themes/classic tab. Alternatively, you could checkout <a href =http://opthemes.com/>Octopress Themes</a> and follow the directions there, most of them have great instructions in the README, just as seems to be the motto of Octopress: Be cool, and credit the author.</p>
Okay! Now it's time for our first post! (Being sure that whenever you get to a stopping point you are uploading to GitHub!)
$ rake new_post  -----And we get to another caveat, my computer does not like the method listed on most sites for this set-up (OS X) and I use "Oh My ZSH" To help with version control.

So for me, I type:
$ rake new_post
prompt: $ Title of my post But first try:

$ rake new_post["Blog of the Future"]
Now you've created some new files. So our friends we've met so far: \_config.yml, .themes, and now let's take a look at source.
\_deploy and public write from source, so leave them be. source/\_posts is where we're headed.
Here, you'll find the-date-in-long-form-your-title and in there you'll find some markdown already filled out for you.
If you use disqus, and set that up in \_config.yml, you can set comments to true. Then write out some html, give it a header, and maybe some nice references to your new sass, then you know the drill, git git git, rake, rake, check!

Next, I'll go over adding a page, particularly an about page, as that is my current battle. I will leave you with this, though, do not mess with any files which you don't understand, if you're messing with the public folder, you will not be a happy lion. Stick with your friends until you get a little comfier in Octopress. Good luck! Comment with any questions! I love to help, and I just *might* have an answer!

Edit: Nope! Went to a Hackathon!

