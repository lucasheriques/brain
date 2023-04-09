# Overview

# Recruiter Phone Interview

# Coding Challenge

see the website for this previous one. TODO my own summary

# Coding Project
- Correctly define the scope. Clarify expected deriverables.

## Additional Deliverables

A few things to include if extra time is available. Good to differentiate myself when compared to other candidates.

### Clarify Requirements
- Specific technology stack? Free to use any JavaScript framework/library?

### Thoroughly Document
- The project reviewer should be able to quickly and easility locate installation instructions for clonning and running the app. This can be a README, PDF document, website, but clarify with the company how they prefer to receive those
- Might be aprivate GH repository; zip file sent through email; hosted as a website with password, etc. Be sure to submit with the proper format and documentation

### Create User Flows
- Sketch user flows for all applications that you create. More of a UX actiiity, however clarifying the information architecture (hierarchy of information throughout the application) and the different flows the user can take (like sign in, edit preferences) will allow you to design your application to fit the users' needs.
- Can include user flows or information architecture within the the final deliverables. Will showcase attention to the end user.
- Use tools like Mural or Figma. Or sketch out on a piece of paper, take a photo and upload

### Additional Enhancements
- Including additional enhancements/features is a great way to impress the potential employer. E.g. on a food tracker app, add the ability to contact the food delivery person through text in order to provide real-time updates
- The feature doesn't have to be fully-functional (can be hard-coded data) but adding these enhancements shows attention to detail
- If there is no time to implement the features, list them with a high-level description of what the features do and why they enhance the UX.

### Note Areas for Improvement
- Always include areas of improvement in the projects. They show a candidate is self-aware and recognizes where he can improve. It's a great way to showcase knowledge without spendijng hours implementing features or refactoring code.
- For example, if you chose to use a UI framework like Material or Bootstrap to ensure it has a consistent and accessible UI, but comes at the expence of app performance and not showcasing CSS skills, this is one area you can note as a future improvement

## Tips for Nailing your Coding Project

- Remove code comments
- Refactor non-performant code
- Test for accessibility (use a tool like Lighthouse or Axe). Fixing small accessibility pitfalls and including a small paragraph explaning your mindful care of accessibility will set you apart from the crowd
- Design a logical project architecture: how to organize the files? camelCase, kebab-case? CSS include the CSS files with the component or separate styles folder? Benefits and drawbacks of each approach? Be consistent with naming and architect the code logically

## Sample Coding Projects

### To-Do Application

Requirements:
- Add tasks
- Complete tasks (mark as done)
- Edit tasks
- Delete tasks
- See how many tasks are remaining

Potential enhancements:
- Animations when tasks are deleted
- Favorite a task and have it appear on top of the list (pin?)
- Create groups or categories of tasks (home, work, etc)
- Light and dark theme (for accessibility)

Deliverables should include:
- Should be hosted with a password to enter. Use Netlify for this.
- Minified and hosted in a private GH repo
- Should provide a README containing instructions on how to install/clone and start your app locally as well as the password for the live site

### Food Delivery App

Requirements for the user:

- See a list of five meal options
- See the prices of each meal option
- Add a meal to the cart
- Change the quantity of melas in the cart
- Remove a meal from the cart
- See the toal bill
- "Check out" - doesn't have to process payment, just display a message stating their order for X price has been received and will arrive in X minutes

Use Figma, Sketch or Illustrator to sketch the UI.

Few enhancements:
- Having restaurants the user can navigate through
- Showing which meal options are vegeratian or vegan
- Show wait time for each restaurant
- Filter by restaurant or meal type

Deliverables same as the previous one.

# On-Site Interviews

Four or five interviews between 45-60 minutes; more than just coding. There are a few different ones, which we'll talk about briefly.

## Data Structures & Algorithms Interview

### Potential Topics

#### Data structures
- Stacks
- Queues
- Linked Lists
- Graphs
- Trees
- Tries
- (added myself) Hash Tables and Arrays?

#### Sorting Algorithms
- Merge sort
- Quick sort
- Insertion sort

#### Searching Algorithms
- Binary search
- Depth-first seach
- Breadth-first search
- Tree traversals

#### Concepts
- Big-O Notation
- Recursion

## Front-End Interviews
Cover web technologies and the question you'll receive likely test practical situations you may encounter during day-to-day responsibilities.

### Potential Topics Covered
#### HTML
- Semantic HTML
- Accessibility / ARIA

#### CSS
- Specificity
- Pseudo-elements / pseudo-selectors
- Position
- Display
- Media queries
- Animations

#### JavaScript
- Data structures (maps, sets, symbols, arrays)
- Closures
- Asynchronous programming
- DOM manipulation
- Event delegations

#### The Internet
- TCP/IP
- CORS
- Performance

#### UX / Visual Design
- Information architecture
- User flows
- UX heuristics

## Sample On-Site Interview
**Infinite Scroll**

How would you design and build an application which is a stream of continuously loading images?

Potential areas to touch:

- **Image performance**: what image should we store to reduce bundle size? Webp is 26% smaller than PNG so might be a good choice
- **Lazy loading**: optimizagion technique where more images are loaded as the user scrols down the page (as opposed to loading 1k images on the first page load). Perhaps as the user near the end of the web page (500px to the end maybe) we make another requests for more images

Other things to keep in mind?

![[Pasted image 20211003203911.png]]

## Sample Process & Communication Interview Questions
Make my own answer for each of those questions.

### Tell me about a project that failed. Why did it fail and how did you handle?
Example answer:
Last year I started a project with the goal of improving mentorship in the tech industry. Unfortunately the project required a lot of my time and I wasn’t able to commit 20 hours a week to keep it running so I had to put it on hold.

I’m still passionate about mentorship so I decided to mentor two developers and write blog posts to share my knowledge. Even though my project is currently on hold I’m able to mentor others through my writing.

I hope to continue the project one day.

---

My answers:

I always wanted to make an application to centralize my financial needs and finally retire my Excel sheet. Also, I would love to have something out there that people are actually using and it helps them in a way.

However, given my current schedule, I don't have the time to dedicate to such a big app. So, what I did instead is started building a couple of small financial tools to calculate things like how much do you need for financial freedom, how much do I own the Receita Federal (Brazilian IRS), etc.

### How would you handle a situation in which your coworker has a different opinion on how to develop a new feature?
Example answer:

I would first try to understand why my coworker is so adamant about their particular solution. I would schedule a time with them one on one where we can discuss the conflict. We would do this in private and at a scheduled time to ensure we’ve created a safe space for a discussion.

What benefits does this solution provide that mine does not? Maybe their solution ultimately is better. If I listen and still disagree I would explain my point of view. If we still can’t come to an agreement we can bring in a neutral party like a team lead to make the final decision.

---

My answers:

Pretty much the above. Discuss the pros and cons with the coworker, one on one, without any previous assumptions. Maybe his solution is seeing something that my does not provide. If I agree - then we are set. If not, I would explain my PoV, and then if we can't decide, bring a neutral party like a team lead to make the final call.

### Why are you looking to leave your current job?
Example answers:

I enjoy my current company but I’m looking to move into a role which allows me to accomplish X. I believe I can do that here.

I’m looking for a company where I can grow my skills through mentorship and continued education (i.e. conferences, online learning platforms).

---

My answers:

## Tips for On-Site Interviews
- Wear Comfortable & Smart Clothing
- Bathroom breaks
- Visit the building the day before if you can

(not really applicable to me because remote is 💖)

## Manager & Team-Matching Interviews
Have a few questions prepared regarding the role. 

- What stack is the team using?
- Does the team iterate on sprints? How long are they? One, two, four weeks?
- What opportunies are there to expand my knowledge? Will I have the opportunity to attend conferences and take online courses?
- Is there an opportunity for mentorship?

Also see [here](https://techinterviewhandbook.org/questions-to-ask/) for more questions.

# After The Interview

Two outcomes: offer or the rejection.

## Negotiating an offer
Salary is not the only thing: PTO, stock options, flexible working hours are others to consider.

### If you're happy with the offer
There's no need to negotiate, but there's also no harm on doing it.

### If you're not happy with the offer
If the company isn't willing to negotiate, you have to decide wether to accept the offer. Every situation is different, so consider your own personal context.

Offer negotiation template:

Hi `recruiter`!

Thank you again for sending me the offer package for a Software Engineering position on `hiring manager’s` team. I'm humbled and thrilled to be considered for this position!

Before I accept your offer, I want to discuss the proposed salary. `Company A` has also given me an offer, however I’m extremely excited about the idea of joining the team at `company` and would like to move forward with you.

I have a lot experience creating/doing `tasks`. Given my experience and expertise I’m seeking a salary in the range of `X` to `Y` gross per year.

I will bring my expertise bridging design and engineering to the team at `company` and will work hard to exceed the team’s expectations and deliver great work!

Please let me know if this salary range is possible. I would love to sign the offer today.

Thank you so much!

## Processing the rejection
Everyone gets rejected. Many times I haven't even got past the initial recruiter phone call. It's a part of the process.