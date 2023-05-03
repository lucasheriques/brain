[Video](https://www.youtube.com/watch?v=4i5iFlP01mQ&t=8s)

Transcription:

Sometimes you can get promoted for being at the right place at the right time. However, we are going to focus on the things that you can actually control.

There are four universal traits of senior engineers.

## First trait: Leadership

Three things people do that get in the way:
1. Biggest reason people struggle with this promotion is because they conflate leadership with management. Senior devs is the first position that is considered a leadership position. You tipically do not have any direct reports.

Leaders set a direction and rally their team to that destination. Managers are concerned with the execution. Leaders can be managers, but managers are not leaders by default.

### An example

Suppose you're on a team that owns a backend service and need to deliver a critical API for a large project with a deadline in a month. A prototype for the call was done with a script, and you realize that the latency for this call is astronomical. Let's say the medium latency is 10s. And this is at or slightly above the threshold for what is acceptable.

An example of leadership would be to do a deep dive and propose that the API should be an asynchronous one where the API surface turn into a submission of work and fetching of status and outputs of drops. This sort of pivot makes the deadline a bit more challenging, but sets your team up for the future as you expect the latencies to increase as extensions are added to the initial functionality. You sell this idea to your team and management. When folks push back, you listen to them and give persuasive data-driven arguments like how a rewrite after delivery will cost more and lead to more operational burden. Maybe your team does not have a good track record of going back and doing things the right way, and there is a large backlog of other items in your roadmap. You write a quick design document and tech spec, break down the tasks and ensure the project is delivered on time despite the extra scope. You communicate the new direction to adjacent teams and they have enough time to integrate.

An example of management would be to realize the API will have high latency but you bias toward fixing it later because this delivery has high visibility and your name attached to it. You don't want to slip. You implement a clever technique to lower latency by 2s on the expected cases. You break the project into components that can be parallelized and follow up on standup to make sure everybody is doing their part. You get a technically deep team member to do a spike on how the API can be rewritten in the future and start to plan on how you will juggle the roadmap to find time to actually rewrite it. After you launch, of course.

If you choose management over leadership, you will think that doing a good job breaking down tasks, being clever, and keeping folks accountable during standups is what senior devs do. They do that, but the critical piece is that they set direction on top of execution. So, if you want to be a senior dev, you need to be opinionated about where your team should be going and your opinions need to be good. 

You can't just be a good coder or an effective scrum master. 

Usually SDEs are always concerned with getting more technical knowledge and to deliver bigger things with their name attached to it.

Being technically deep is a universal trait of senior engineers, but not sufficient for getting to the next level. These sort of responses are missing the point. All SDEs are technically deep and ship things. Technical chop and project management will only get you so far. For true tech depth, you need a layer of in leadership.

When you go into a meeting with engineers you've never met before, your level and title are not part of the meeting invitation. But, as the meeting progresses, you get to know who the seniors are. That's my litmus test for senior engineer. When folks in the meeting assuming someone is a team lead because of the way they carry themselves and the way they talk about things. If folks only realize that they aren't a senior engineer until afterwards, when they look them up, that's a key indicator that you're ready. To tell is that they demonstrate they are thinkings about the long-term consequences of immediate action and communicate a steady state for systems that's healthy, makes sense, and doesn't compound existing operational burden or tech debt.

Tech promotions are almost universally anti-peter principle. The peter principle is the idea that if you're killing it at your current level you deserve a promotion to the next level. On the surface this seems like a reasonable way to approach promotions. The problem is that you find the correct level of a person only by promoting them to a level where they become incompetent. Their proper level is therefore one level down.

There are no demotions in tech. There are only improvement plans and termination. This leads to a culture where companies are really conservative with promotions and they only promote folks that are already demonstrating they're operating at the next level. They can still have gaps at the next level, but they have to be clearly demonstrating the next level traits.

## Second trait: rejection of the hyperbolic discounting

Hyperbolic discounting is a fancy term for preferring immediate benefits at the expense of future benefits, even if the future benefit is large. Thus, people discount the size of future returns. There are immense pressures to deliver soon and the temptation to realize an immediate gain is often a team's default trajectory.

But what if you didn't discount the future? What if your time horizon is not the next two sprints, but rather 12 months? This is not unreasonable, because you will probably be on the team in twelve months.

If your frame is to maximize the benefit of your team's actions over the course of a year, how would that affect today's choices?

**Living in the future takes time. You have to think about it, a lot.** Your ideas can't be half-baked. If you make an impassioned plea to re-architect your systems and your team does it, they're going to expect a payoff. Things are worse, you are in deep doo-doo. So it'll take time and energy on top of your existing duties to do deep designs and analysis. You don't put the time in, you will lose credibility and people will learn to ignore you.

So, you have to make more time. There are two ways to do this:

You can put more hours in on nights and weekends. 

Seems like an attractive option, because you probably have had to put time in on nights and weekends to meet a tight deadline before. You've been doing this since you college on your bootcamp. But this is an example of hyperbolic discounting, just applied to your life instead of your team. It's not sustainable. Relationships with friends and family will suffer and you won't be taking care of yourself. Worse, when you get promoted, you won't have the tools to cope with your new responsibilities. You'll burn out, get divorced, not see your kids, and become so toxic that work will fire you. **Don't take this faustian bargain.** You'll end up bitter and an unhealthy person. 

So, to find time and think about the future, you need to extract more time from your existing working hours. There is no other healthy way.

There's no shortage of advice on how to manage time out there, and I've tried them all. Yes yes, you should decline all superfluous meetings, set timers, block off time on your calendar, stop going to social media and Reddit, delegate tasks, etc. What you're going to find though, is that there are tasks that only you can do on your team. You're the only one that knows how to build an old package, or you take all of the interviews for your team or you're the only one that knows the ins and outs of a legacy piece of code, you're the only one that breaks down tasks well. The trick is to grow others around you. It requires more bandwidth in the short term, but pays off in the long term. That's two birds with one stone.

**Growing others is the last universal hallmark of a senior engineer.** You know you've grown others when you freed up your own bandwidth. If you use the bandwidth to design the future, we've come full circle.


## Recap

Senior engineers have four universal characteristics. 

| Universal Trait                       | Pitfall                                                                                                        |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Technically deep and deliver on time. | 1. Over-indexes on delivery and tech depth. Make sure this box is checked, but be aware too much time spent here.                                                                                                        |


 
> Faustian bargain: a pact whereby a person trades something of supreme moral or spiritual importance, such as personal values or the soul, for some worldly or material benefit, such as knowledge, power, or riches.


🚫
"Three things people do that get in  the way of becoming a senior engineer: not taking ownership, not being proactive, and not having a long-term vision."
💼
"The biggest reason people struggle with this promotion is because they conflate leadership with management."
💡
Being a leader means making tough decisions that may make the deadline more challenging, but ultimately set the team up for future success.
🐄
Technical chops and project management are like adding more cowbell to a song that has enough cowbell - true tech depth requires a layer of leadership.
💼
Tech promotions are anti-peter principle, meaning promotions are conservative and only given to those who are already demonstrating the traits of the next level.
🕰️
"If your frame is to maximize the benefit of your team's actions over the course of a year, how would that affect today's choices?"
⏰
Working longer hours is not sustainable and can lead to burnout, negatively impacting personal relationships and overall health.
🐦
"The smartest way to invent more time is by growing others around you to take over their existing responsibilities."
