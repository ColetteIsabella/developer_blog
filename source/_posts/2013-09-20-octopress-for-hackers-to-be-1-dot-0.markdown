---
layout: post
title: "Octopress for Hackers-To-Be 1.0"
date: 2013-09-20 16:34
comments: true
categories: Jekyll, blogging, Octopress
---
<header>
<h1>Let's Create an Octopress Blog!</h1>
</header>
<body>
<h4>* $ means that you are entering a command into console.</h4>

<p>Two months ago, I had no idea what a console was, what my husband or my father were talking about, when they told me about their work, commands and structures and Agile and... My dad's a Java Engineer, and my husband is a UX Designer.
<p>I started playing with <a href= http://www.codecademy.com/>Code Academy</a> Then I realized, this is how I think! Even better, I found <a href= https://www.codefellows.org/>Code Fellows</a>, in Seattle. I took their bootcamp on Ruby on Rails, and boom, life => changed.</p>
<p>But that's not why you're here, you want to know how/why/what you're reading. Maybe you're curious about starting your own all-you designed blog, maybe you've heard of <a href= http://octopress.org/>Octopress</a>, either way, this is how a noob with a Ruby understanding, made this:</p>
<p>First off, I cannot emphasize enough the importance of Reading Everything. If you have even a marginal understanding of code, and you try running at this with just that, a lot of complications will slap you in the face.</p>
<p>I also recommend the IRC channel #octopress, for anything you get stuck on. But let's try to avoid complications. With all luck, you won't run into any problems, but since I did, I will show you mine, and you can skip the ones you don't have and ask about ones I didn't run into. (A substantial amount of coding, is messing up)</p>
<h3>I'm assuming you have git, Ruby, and RVM or RBENV installed. And you need to use ruby version 1.9.3 for now, check it with *$ruby --version</h3>
<p>So let's get statrted.</p>

 <h3>The install process:</h3>

  <p>Following the directions from the page, it recommends a clone. This is what I used, and it was quite clean, but forking their repository is also a valid method, here are the differences:</p>
  <p>If you choose to clone, you will cd into your Dev directory (you should have a designated Dev directory to reduce confusion.)Copy this in to that directory:</p>
  <p>git clone git://github.com/imathis/octopress.git octopress</p>
  <p>Then you need to switch into the octopress directory using:</p>
  <p>$cd octopress</p>
  <p>The documentation recomends you check your Ruby version here, just know that if you are not in 1.9.3, you might not get the results you want.</p>
  <p>Next, you'll type</p>
  <p>$gem install bundler</p>
  <p>If you are using rbenv, you'll want to run</p>
  <p>$rbenv rehash</p>
  <p>Then $bundle install</p>
  <p>$rake install</p>
  <p>This is where it gets fun, and this is where we need to stay calm. There are a few ways this can go: it could show up brilliantly with the deafult interface saying- Your Octopress Blog, Or, it could be sparce and look a lot like html with no CSS structure.</p>
  <p>Either way, let's start with our new favorite file: config.yml. It looks like this(with examples):</p>
  <p>url: your_website.com</p>
  <p>title: The Cheese Blog</p>
  <p>subtitle: Cheese should not be orange, or bouncy</p>

  <p>author: Richard Ayoade -not actually him-</p>
  <p>Below that:</p>
  <p>root: / <= it should be that unless you have a special, different route. </p>
  <p>permalinks: (leave this alone unless you know what you're doing)</p>
  <p>source: source</p>
  <p>destination: public/ <= It might automagically add your github repo, don't keep it. it's a trap!</p>
  <p>Now some decisions come up, I chose<a href=http://octopress.org/docs/deploying/github/> Github Pages</a>, it's easy, and I'm used to it. But that didn't make it simple.</p>

  <p>There are other particulars to watch out for with Heroku and Rsync, but since I didn't use them, I'll go through gh-pages.</p>
  <p>First off, you want to create a Github Repository, if you cloned in, it should be set up, but launch GitHub and check to make sure your initial commit was successful.</p>
  <p>Then, you use the rake configuration to get your pages set up:</p>
  <p>$ rake setup_github_pages</p>
  <p>Easy peasy, right? It asks for your Repo url, and then should do some other things...Well you'll want to check those went through before you go all gung ho on this.</p>
  <p>Make sure that your new origin was created by typing:</p>
  <p> $git remote -v You should see:</p>
  <p>octopress git://github.com/imathis/octopress.git (fetch)</p>
  <p>octopress git://github.com/imathis/octopress.git (push)</p>
  <p>origin git://github.com/your/repo.git (fetch)</p>
  <p>origin git://github.com/your/repo.git (pull)</p>
  <p>If you only see the first 2, DON'T PANIC, you just need:</p>
  <p> $git remote add origin git@github.com:username/username.github.com.git</p>
  <p>Now you need to create a source directory in your repo to work from **Wait! What happened to Github Pages?!?** Believe me, this will go a lot smoother if you set all this up now.</p>
  <p> $git branch</p>
  <p> Should say: master</p>
  <p>$git branch -m master source</p>
  <p>$git branch</p>
  <p> Should say: source. Hooray! This set up your _deploy branch, which will become near and dear.</p>
  <p> If you have a custom domain you want to run your site on, it's an awkward, but doable set of steps.</p>
  <p>First, register your Domain with whoever. Seriously, whoever.</p>

<h4>Note, I just heard an interview with Richard Ayoade, where he talked about cheese, apologies, it's just on my mind.</h4>

<p>Once you have whitecheeseforever.org, you'll want to go into the DNS settings on your chosen page. DNS means Domain Name System, so even though it sounds like a scary techy term, it's quite asinine.</p>
<p> Here's what you want to change:</p>
<p>whitecheeseforever.org  - A - 204.232.175.78</p>
<p>(Different sites give different numbers, but this is the one which I see most often, and which seems to work for me.)</p>
<p> If you want it to redirect from www.whitecheeseforever.org, you will also want:</p>
<p>www.whitecheeseforever.org -CNAME- username.github.io</p>
<p>This will take a while to kick in, so don't get too excited, instead, go back to your console and type:</p>
<p> $echo "whitecheeseforever.org" >> source/CNAME</p>

<h4>Okay, yeah, the cheese thing got a little old on me too...</h4>

<p>Hooray! There's now a new file called CNAME in your source folder. Go make sure there is only ONE domain name in there. Just the one with no www. Go ahead, I'll wait. Just one? Then onwards to greatness!</p>
<p>Now back to console, and hit:</p>
<p> $rake generate </p>
<p> $rake deploy    And you're running! Tomorrow, we'll write our first blog post, check our themes, bug check, wonder why it doesn't work, wonder why it works, then show the world our Hacker skillz!</p>
<p>For now, you need to wait for your DNS to catch up, and I need to feed my impatient cats, who will never understand why I use their warm bed to click all day.</p>
<p>Until tomorrow!</p>
</body>
<footer>
<div id="disqus_thread"></div>
<script type="text/javascript">
        var disqus_shortname = 'anatomyofaprogrammer';

        /* * * DON'T EDIT BELOW THIS LINE * * */
        (function() {
            var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
            dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
            (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
        })();
    </script>
    <noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>

  </footer>
