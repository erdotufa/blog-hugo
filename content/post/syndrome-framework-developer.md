---
title: Syndrome of the Framework Developer
subtitle: If the only tool you have is hammer, you tend to see every problem as a nail! Abraham Maslow
date: 2020-05-18
draft: false
tags: ["Software entropy", "Software design", "Design patterns"]
bigimg:
  [{ src: "/img/miops-trigger-552190-unsplash.jpg", desc: "The golden hammer" }]
---

<br/>

> "Software developer because superhero isn't an official job title"

After a little experience in software, sometimes as Developer we feel like superheroes (and we are!); maybe that happens after reading a book about design patterns, clean code, following blogs, twitter or famous people known in a conference;
but we forget completely that we have our own brain, and then the most import thing:

> the context of our product!!!

Filled with enthusiasm, we start to think every line of code about design pattern, and we develop everything thinking as it's a framework.
If the project is small and hasn't a very big evolution, it could be a good idea to make little experiments, and try to find new approaches or coding strategies.
In complex projects, or in ones that became complex very quickly, working on that mode could be very dangerous and creates "Needless Complexity”.

You have to be more pragmatic, able to put things at the right place in its larger context, always trying to be aware of the bigger picture. If not you will find yourself jamming pieces of puzzles that can’t be put together, wasting your time and effort. You will feel like [squaring the circle](https://en.wikipedia.org/wiki/Squaring_the_circle), and sometimes for things that really don’t matter.

To complicate something which is simple is always possible, but what happens if the project grows very fast, and we have to add new functionalities?
Needless complexity, if not necessary, can bring you into the wrong design of the software, and make our life a nightmare, if we need to maintain and add new functionalities.
Our design becomes rigid very quickly and our code ["Legacy Code"](https://en.wikipedia.org/wiki/Legacy_code), and then we have built the famous [“big ball of mud”](https://en.wikipedia.org/wiki/Big_ball_of_mud).

It is easier to evolve the design of an app, and to find the right architecture while the real complexity grows, or to do it during a phase of refactoring, separating the code, building new layers but at the right time. This is better than trying to put together something that became unnecessarily complex and widely spread.

Often people with this syndrome make an extreme separation of concerns, but after there is no reuse of code! (!!! I'm not speaking about separation of methods inside a layer to favor the reading or reduce the complexity of the method, rather the code spread in hundreds utilities or services inside the project)

The main goal of the design patterns (for example the [Strategy](https://en.wikipedia.org/wiki/Strategy_pattern)) is to create an abstraction to facilitate the reuse of the code, reducing the duplication. If there is no reuse of code, is it really necessary to overthink for a design, trying to predict the future (if a meteor will fall down), after that to discover that our design is wrong because the requirements always change in an unpredictable way, very differently than we were thinking?

Have you ever looked inside your favorite framework/library? Is it always as clean as you think? Or usually they follow or have followed an evolution in time?

Have you never thought:

> I don't understand why they didn't implement that pattern?

And after one year look again, and see it implemented because they follow an evolution? I personally saw that many times!

Maybe a classic case is to imagine something very complex at start, look at the code and think:

> mmmhhhh what, that's it? I thought it was more complex than that instead...

One frequent comic thing that happens and that I have done at the start of my career is:

- you find a new solution somewhere
- you can’t wait to implement it, filled with enthusiasm like you are going to save the world as in The Armageddon movie
- you work hard to make a big refactoring maybe for days like mad

At the end of your work satisfied you look at the result thinking:

> what a cool thing I have done!!!

But when you look at the whole context, your face changes and you think:

> It looks the same as before, or, it is not as cool as I thought at the beginning

If you recognize this symptom (or you know someone who has it), it simply means that you don't have a great experience or you still aren’t a ["software craftsman"](https://en.wikipedia.org/wiki/Software_craftsmanship).

This syndrome is also recognized in psychology as the [Dunning-Kruger effect!](https://en.wikipedia.org/wiki/Dunning%E2%80%93Kruger_effect)

From Wikipedia

> In the field of psychology, the Dunning–Kruger effect is a cognitive bias in which people with low ability at a task overestimate their ability. It is related to the cognitive bias of illusory superiority and comes from the inability of people to recognize their lack of ability.

Where to start if you recognize yourself with this syndrome?

Stop adding needless complexity, until you really need it! Even if it is not really simple to be aware of that, because at first we always think that we are right.
Make changes as your software evolves and the requirement changes.
The best way is just sometimes to start to do things differently but not always. As Al Pacino in “Any Given Sunday” in his motivational speech says:

> “We can fight our way back into the light. We can climb out of hell.
> One inch, at a time.”

This is the right way forward, because to become a master it requires:

> Calm, Patience, Passion and Time (CPPT).

Resources:

- Look inside your favorite library/framework
- [Agile Principles, Patterns, and Practices in C#](https://www.amazon.com/Agile-Principles-Patterns-Practices-PRACTS-ebook/dp/B0051TM4GI/ref=pd_sim_351_6/164-0957370-8645367?_encoding=UTF8&pd_rd_i=B0051TM4GI&pd_rd_r=134300eb-4ff9-11e9-8022-3521c0a11248&pd_rd_w=nmGxL&pd_rd_wg=Y5rKm&pf_rd_p=90485860-83e9-4fd9-b838-b28a9b7fda30&pf_rd_r=54RSWYMDBT3C948FKKTX&psc=1&refRID=54RSWYMDBT3C948FKKTX)
- [The Pragmatic Programmer: From Journeyman to Master](https://www.amazon.com/Pragmatic-Programmer-Journeyman-Master-ebook/dp/B003GCTQAE/ref=sr_1_1?crid=ZLB6UVU0XX93&keywords=pragmatic+programmer&qid=1553626834&s=digital-text&sprefix=pragmatic%2Cdigital-text%2C223&sr=1-1)

Photo by MIOPS Trigger on Unsplash
<a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px" href="https://unsplash.com/@miops?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from MIOPS Trigger"><span style="display:inline-block;padding:2px 3px"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-2px;fill:white" viewBox="0 0 32 32"><title>unsplash-logo</title><path d="M10 9V0h12v9H10zm12 5h10v18H0V14h10v9h12v-9z"></path></svg></span><span style="display:inline-block;padding:2px 3px">MIOPS Trigger</span></a>
