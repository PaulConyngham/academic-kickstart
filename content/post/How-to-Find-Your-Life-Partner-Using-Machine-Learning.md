+++
title = "How to Find Your Life Partner Using Machine Learning"
date = 2019-03-05T07:56:25+11:00
draft = false

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = []
categories = []

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
[image]
  # Caption (optional)
  caption = ""

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = ""

+++

![alt text](https://i.ibb.co/3stHTs2/il-794x-N-1342471817-52h4.jpg)

&nbsp;

## Exploration vs Exploitation
---


There is this age old problem in machine learning and it goes something like this.

Let’s say you are on the hunt for a hot date with the eventual goal of picking up a life partner.

First you hop on your favourite dating app of choice.

After chatting to a few people you manage to score yourself a date. The way they were coming on to you so strongly on the first date was a was a bit weird, strike out, you decide that’s it for the online dating person.

The following week you decide dating apps are kind of lame, so you head out to the bar.

You manage to work up the courage to approach someone and after talking to them for a bit realise that this person has really bad breath and might not be quite the right person for you.

Finally, towards the end of the night and after a few drinks, you work up your last bit of courage to go over and talk to an attractive person, who has been looking at you over their shoulder all night.

You hit it off and get their number. Two years later you are in a relationship and decide to get married, happily, ever after.

What has any of this got to do with Machine Learning? Well, actually, the Exploration vs Exploitation problem is as old as the field of ML itself.

That is, how much time do you spend “exploring”  the options available for solving a particular problem, in this example going on dates with people to look for a partner -


Versus,

How much time do you spend, ahem, “exploiting” a particular solution to a problem - being in a relationship with someone.

To make the idea of Exploration vs Exploitation a bit more [**concrete**](https://www.youtube.com/watch?v=5ZNJPSe1nZs), let us examine a few more examples:

Take choosing a career - how much time do you spend looking at potential job opportunities - exploring - vs being in a particular job - exploiting.

Or being a stock trader, how much time do you spend researching different trading techniques - exploring - before you decide to choose a particular trading stack - exploiting.

For that matter, take work in general. You could spend time on Facebook, Linkedin, Twitter exploring or you could buckle down and get exploiting the task you should be doing right now.

&nbsp;

## Enter Epsilon-Greedy
---

We have seen that the problem of Exploration vs Exploitation occurs all over the place & is not limited to Machine Learning.

However, it just so happens that the Machine Learning world has devised a solution to the Exploration vs Exploitation problem.

We call a simple algorithm that solves this problem “Epsilon-Greedy”.

The name is irrelevant, however the underlying principle is deceptively simple and it is this principle that I would like to share with you in this post.

The main idea with Epsilon-Greedy is that given any problem, you spend some time exploring all the options that are available to you to solve that problem.

Once you have found an option that gives you the highest average reward, you continue to exploit that option.

That’s all there is too it.

>"The main idea with Epsilon-Greedy is that given any problem, you spend some time exploring all the options that are available to you to solve that problem. Once you have found an option that gives you the highest average reward, you continue to exploit that option. "

How would the world be if everyone valued the idea of Epsilon-Greedy as a universal principle rather than some obscure algorithm hidden in the pages of text book somewhere? Let’s take a minute to appreciate just how powerful the concept of Epsilon-Greedy really is.

Imagine if you are a student just starting out your first year of university. If you found that you were not good at a particular subject and you had Epsilon-Greedy as a valued principle, you would not care as much if you successively dropped courses because after all - you are just exploring. After exploring for a while you might just stumble upon a career path that may be more suited to you, which you could exploit - for higher average satisfaction over the course of your life.

Or take it back to the dating example used at the start of this post. If you had Epsilon Greedy as one of your principles in your dating toolkit, would it not be so troubling if you knew that first you were going to first try a couple of different date options first before you decided to jump into a relationship with someone?

&nbsp;

## Algorithms, Axioms or Discoveries?
---

Up until now most people have treated machine learning algorithms as essentially obscure mathematical notation to be hauled out of dusty textbooks from time to time to solve case specific issues.

If we realize that these same algorithms address fundamentally human issues however, such as choosing when to explore and when to exploit, we can start treating algorithms as “field tested” principles that exist in nature herself - that we can all adopt & start living our lives by.

In summary, the key idea to be learnt from the Epsilon-Greedy algorithm is that it really does pay to spend some time discovering and sampling potential options available to solving a problem, before we go all out and exploit a solution to that problem.

~

If you would like to deep dive into how the Epsilon-Greedy Algorithm works, feel free to read my other [much longer post explaining just this](https://star-ai.github.io/What-the-Shell-is-a-Multi-Armed-Bandit-Guest-Starring-the-Epsilon-Greedy-Algorithm/).
