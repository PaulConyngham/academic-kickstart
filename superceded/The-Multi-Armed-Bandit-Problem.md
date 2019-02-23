+++
title = "The Multi Armed Bandit Problem"
date = 2019-01-27T21:40:56+11:00
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

#What the Shell is a multi armed bandit? Guest starring the Epsilon-Greedy Algorithm.

###### Intro to Reinforcement Learning by Paul Steven Conyngham

#Bandits!

![alt text](https://i.ibb.co/N9ff6tt/what-the-shell-by-paul.png)



Machine learning people love to give fancy names to things so that no one can understand what they are on about.

For someone relatively new to machine learning, "The multi armed bandit problem" sounds just like one of these fancy names.

Do not fret however. The point of this blog post is to explain exactly what a Bandit is and most importantly, why it is usually used as the starting point for anyone looking at learning Reinforcement Learning.

So then, what the shell is a bandit?

This.





![alt text](https://i.ibb.co/xHx2jFt/Screen-Shot-2019-01-18-at-8-29-44-pm.png)

A bandit is an old fashioned american name for what we usually call a "slot machine".

Here in Australia we like to call it the "pokies".

Great, but what the shell is a multi armed bandit?

Simply, this:

![alt text](https://i.ibb.co/Cmm0NLn/Screen-Shot-2019-01-18-at-8-38-17-pm.png)

A whole bunch of "bandits" stacked together such there are many "arms" to pull. This is where the "multi armed" part comes in.

![alt text](https://i.ibb.co/8K8pbwx/multiararmedbandit-what-the-shell.png)

Hold up.

Why are we talking about slot machines with regards to machine learning?

Well, one definition for Reinforcement Learning, the subfield of machine learning that we are talking about here deals with:

>"Finding the optimal strategy to solving a problem in the face of massive uncertainty."

Let's see why this is important by expanding on and explaining this definition a little bit further by considering an example.



Lets say you wanted to drive your car from your home to your work.

Along your way you are not quite sure what the traffic lights will be doing or what the other cars will be doing. You could encounter 5 other cars that delay you at a roundabout, or you could encounter 10 red traffic lights in a row.

This is the uncertainty part in our definition above.



![alt text](https://i.ibb.co/Pr2wZ0t/Screen-Shot-2019-01-18-at-8-58-08-pm.png)



We also need a **_plan of what we will do_** once we encounter the intersections, roundabouts & traffic lights as we drive our car on our way to work.

This plan or **_strategy_** is what reinforcement learning aims to figure out. Even more specifically, reinforcement learning attempts to learn the **_optimal strategy_** -  that is to say, the best possible strategy for a specific task (in this case, the best possible way of driving through all the obstacles of traffic lights, roundabouts etc from home to work.)

So this is the **_strategy_** part in our definition above.

___

###### Reinforcement Learning Terminology Decoded #1:

In reinforcement learning the name given to the strategy that we are following to solve a given problem is called a **_policy_**.

(so that is your first bit of fancy reinforcement learning terminology decoded).

Following the previous example of driving to work. An example of a **_policy_** would be driving as fast as possible to work (this is our strategy).

Another example of a **_policy_** would be to ignore all red lights (again this could be another strategy).


(Of course your policy could also be something boring. For example, only moving on green traffic lights, stopping for all other cars at roundabouts like I hope you are doing... etc)

___

Now we know that we are dealing with finding best strategies (_policies_) in the face of unknown conditions (_uncertainty_).

The multi armed bandit problem is usually brought up as the starting point of most Reinforcement Learning (RL) text books because it introduces several core RL ideas.  The first of which is that in slot machines - you are dealing with _uncertainty_.

In other words - if you go up to a slot machine and pull the lever, you have no idea when you are going to get a cash payout.

We also examine the multi armed bandit as our "toy" problem for learning Reinforcement Learning because it teaches us the second core concept with regards to RL. That is, what to do when we have more than one option for solving a problem. 

How do we decide upon the right strategy for how & when to pull the many different levers of our multi-armed bandit or in terms of our machine learning terminology from before - aka, the best “policy”.

The bandit problem in a nutshell - what do we do when we have more than one slot machine to choose from and we would like to know which slot machine is going to give us the biggest average payout or **_reward_** over time. In other words which slot machine is the best choice?

Lets get cracking on this problem by introducing another Machine Learning idea and your first (baby) Reinforcement Learning Algorithm.


#Exploration vs Exploitation

There is this age old problem in life and it goes something like this.

![alt text](https://i.ibb.co/FqrfDc7/itsamatch-1.jpg)



Let’s say you are on the hunt for a hot date with the eventual goal of picking up a life partner.

First you hop on your favourite dating app of choice. 

After chatting to a few people you manage to score yourself a hot date. The way they were coming on to you so strongly on the first date was a was a bit weird, strike out, you decide that's it for the dating app person.

The following week you decide dating apps are kind of lame, so you head out to the bar.

You manage to work up the courage to approach someone and after talking to them for a bit begin to realise that this person has really bad breath and might not quite be the right person for you.

Finally, towards the end of the night and after a few drinks, you work up your last bit of courage to go over and talk to an attractive person, who has been looking at you over their shoulder all night.

You hit it off and get their number. Two years later you are in a happy relationship and decide to get married, happily, ever after.

![alt text](https://i.ibb.co/dktFB3V/in-love-1071325-960-720.jpg)



What was just described above is an age old problem in machine learning.

How much time do you spend **"exploring"**, (going on dates with people looking for a partner etc),

Versus,

How much time do you spend, ahem, **"exploiting"** (being in a relationship with someone etc.)

~

Lets make the topic of exploration vs exploitation more [concrete](https://www.youtube.com/watch?v=5ZNJPSe1nZs) with a few more examples.

Another example of EvE is how much time you spend looking at potential job opportunities (exploring) vs being in a particular job (exploiting).

![alt text](https://i.ibb.co/Tty4PWy/Screen-Shot-2019-01-18-at-9-47-26-pm.png)



Yet another example would be if you are a stock trader. How much time do you spend searching for the best trading strategy (exploring) vs implementing a strategy on the stock market (exploiting).

The reason we consider the exploration vs exploitation idea on the multi armed bandit problem, is that remember there is more than one machine and ***each slot machine's is tuned slightly differently***, such that each slot machine will give different average cash payouts.

**So how then do we go about discovering which Bandit pays out the most?**

Well, if you have not guessed it already, what we would like to do is spend some time **_exploring_** - to see amongst our many slot machines, which slot machine gives the best average payout.

When we have discovered which machine gives the best average payout, we then want to keep **_exploiting_** this machine.

Ok then. Time for your first RL (baby) algorithm


#The Epsilon-Greedy Algorithm

Simply, the Episilon Greedy Algorithm is this:

![alt text](https://i.ibb.co/4TPp8h2/Screen-Shot-2019-01-19-at-1-02-05-pm.png)

Seriously though, if you did not understand that no dramas at all. 

The rest of this post is going to be about breaking apart the mathematical notation above into a more human readable format (HRF) :). Let's do it.

Lets say we wanted to implement some kind of **Exploration vs. Exploitation** on a problem.

How would we do it?

Let's examine the multi-armed bandit problem in a little bit more detail, to explain what **_epsilon_** & **_greedy_** is and why we are examining the multi armed bandit problem in the first place.

Say we have a bandit (slot machine) and that if I pulled the lever on the bandit 200 times, I would get data of the payout of that slot machine that looked like a bell curve like so:

![alt text](https://i.ibb.co/v4S6XKH/Screen-Shot-2019-01-21-at-7-50-39-am.png)

*Figure 1. Average payout of a slot machine based on the amount of times that the lever has been pulled. For example, we can see that at around the $70 mark the lever on the slot machine has been pulled around 44 times.*

The middle of the bell graph in figure 1 is centered around the 70 dollar mark. We can therefore say that our slot machine in the graph in figure 1 has an average payout of around 70 dollars. 



___

######Reinforcement Learning Terminology Decoded #2:

In machine learning we use another name for the **bell curve** (pictured below). That name is the "**normal distribution**". This is technically more correct as we will see soon.

Key idea: "A distribution is usually "centered" around an average number."

![alt text](https://i.ibb.co/k3vDq8m/Screen-Shot-2019-01-21-at-7-55-09-am.png)

_Figure 2: Normal distribution centered around 100._

___



Every time we pull our lever on the bandit, it will give a different cash payout .

In figure 1, sometimes it will be 65 dollars, sometimes it will be 80, but the average payout over time will be $70. This is the centre of our distribution.

A slot machine is meant to be **_random_** -  and we would like to discover a pattern in the “random” data if it exists. 

We use the idea of a **_distribution_** to represent our Bandit's distribution of possible cash payouts. In essence the distribution is represting **_uncertainty_**.

Now let's examine the case of two slot machines.

Each slot machine will each give payouts according to two **_different normal distributions._**

What does this mean? Have a look at the image below:



![alt text](https://i.ibb.co/1dsQtvS/Screen-Shot-2019-01-21-at-8-02-59-am.png)

_figure 3, Here we can see that our first bandit, the bandit in blue,  which had an average value of  70 - is centered around the 70 dollar mark._

The bandit in pink in bandit #2.

We ***sample*** Bandit #2 to collect more data by pulling the lever on Bandit #2 over and over and collect the new data on how Bandit #2 performs, seen in figure 3.

When plotted, we can see that bandit #2 has a ***different distribution*** and has a average payout centred around the $65 mark.

We have now introduced two bandits, bandit #1 & bandit #2.

We have also learned that each bandit has a different distribution.

Why is this important?

By “sampling” each bandit and building distributions, **we were able to determine which one of our bandits paid out the most money.**

The answer, if you have not guessed it already, is that Bandit #1 wins - with an average payout of 70 dollars as opposed to bandit #2, only paying out on average 65 dollars.

Linking back to what we talked about earlier, what we were doing by sampling each bandit and building distributions was ***doing the exploration phase of the Epsilon Greedy algorithm.***

In summary,

Given a problem with many options. 

What we would like to do is explore all the options available to us by randomly sampling between the different options available, over and over until we start to build up a distribution for each option.

Gather data on option 1 (Bandit #1), then a little bit of data on option 2 (Bandit #2) over and over until we have built distributions for all of our options.

We then calculate the average seperately for each distribution available to us to discover the best option.

Once we have discovered the best option we can continue to ***exploit it.***

Let's now see where  **Epsilon** comes in.

# Epsilon

------

###### Reinforcement Learning Terminology Decoded #3:

According to wikipedia Epsilon is the 5th letter of the Greek alphabet and looks like this:

### ε

Hieroglyphics right?

------



Epsilon is a greek letter. But what epsilon is used for is the interesting bit.

When ***sampling*** Epsilon controls the ratio between the amount of time we spend exploring vs how much time we spend exploiting.

Think of epsilon as a volume knob, which you are able to turn that controls the amount of exploration you do versus the amount of exploitation.

Initially we want to explore as much as possible that is, set Epsilon to one.

So when ε = 1, exploration is maximised.

when ε = 0, exploitation is maximised.

How then do we go from an epsilon of 1 down to 0?

Well, one way to do it is to choose a mathematical function. 

There are many mathematical functions you can use to control Epsilon. However in this example we are going control Epsilon using a linear function...or more commonly known as a straight line

Think of the linear function is the volume knob controlling the ratio between exploration and exploitation.

From high school mathematics, a straight line has the form y=mX+c

 As we slowly start to figure out what is the best possible option to be using to solve a problem via sampling, we turn up the Epsilon volume knob. This decreases the amount of exploration we are doing and starts focusing in on the best solution we have found so far to solve a given problem.

Taking this back to our toy problem of bandits, we first start exploring by pulling different levers at random between Bandit # 1 and Bandit # 2.

Following this random sampling process, we will start to see which distribution is going to give us the biggest average payout or reward. 

Simultanously as we are sampling, we start to decrease epsilon and start focusing on the option (bandit) that is going to give us the biggest reward (payout).

