---
title: "Nobody Actually Uses Their High School Computer Science Class"
date: 2025-11-21
author: "Kadin DeMarche"
tags: ["education", "programming", "learning"]
excerpt: "High school CS teaches Java and sorting algorithms. Actually building stuff requires JavaScript, APIs, deployment, and none of that. Here's where the disconnect is."
---

# Nobody Actually Uses Their High School Computer Science Class

Our high school offers AP Computer Science. It's taught in Java. They cover object-oriented programming, data structures, and algorithm complexity. If you do well, you can pass the AP exam and maybe get college credit.

Im taking it. I have an A. Don't use anything from it. Do I understand Java? Yes, but thats from me making my own Minecraft Plugins...

This isn't the teacher's fault. The curriculum is fine if your goal is passing the AP exam. But if your goal is actually building things, there's a huge gap between what schools teach and what you need to know.

## What They Teach

**Java fundamentals:**

- Classes and objects
- Inheritance and polymorphism
- ArrayList, HashMap, basic data structures
- Sorting algorithms (bubble sort, merge sort, quick sort)
- Big O notation
- Recursion

**The AP exam tests:**

- Reading Java code and predicting output
- Implementing methods that follow specifications
- Understanding object relationships
- Debugging provided code

It's all theory and isolated problems. "Write a method that returns the kth largest element in an array." You're given method signatures and expected to implement them in 30 minutes.

Nothing wrong with this as an academic exercise. Understanding data structures matters. Algorithm analysis is useful.

But it's completely disconnected from building actual software.

## What You Actually Need

Here's what I needed to know to build my projects:

**For Slate (job platform):**

- How to set up a Node.js server
- Express.js routing and middleware
- How APIs work (REST, endpoints, HTTP methods)
- Authentication (JWT tokens, session management)
- Database queries (SQL or MongoDB)
- Frontend-backend communication
- Deployment (AWS, Vercel, environment variables)
- Git and version control

**For MarkSite (static site generator):**

- Reading and writing files in Node.js
- Parsing Markdown and frontmatter
- Template engines (Nunjucks)
- Command-line arguments and CLI tools
- Package.json and npm publishing
- How to structure a distributable Node package

**For this blog:**

- GitHub Pages deployment
- DNS and custom domains
- Basic HTML/CSS/JavaScript
- How the browser renders pages
- SEO basics (meta tags, sitemaps, structured data)

Notice what's missing? Sorting algorithms. Big O notation. Writing Java classes.

The skills from AP CS aren't useless, but they're like 5% of what you need. The other 95% is stuff they don't teach.

## The Self-Taught Path

Everything useful I know came from building things and googling (shoutout stack overflow my absolute goats) when I got stuck.

**How I actually learned:**

1. Had an idea (build a job platform)
2. Started building, immediately hit a wall
3. Googled "how to make a node.js server"
4. Copied code from tutorials, broke it, fixed it
5. Googled the next error message
6. Repeated until something worked

This is messy and inefficient compared to a structured course. But it teaches you what you actually need, when you need it.

The school approach is the opposite: here's everything you might need someday, memorize it for the test. Then when you actually build something, you've forgotten half of it and the other half doesn't apply.

## Where CS Education Gets It Wrong

The disconnect isn't just high school. College CS programs have similar issues. They teach algorithms, theory, and fundamentals but skip the practical stuff (I know this since I have a ton of friends who are taking classes at community college outside of HS, I still know more than them and the have been in the system for a whole year more than me).

**Problems with the current approach:**

**1. Wrong language focus**
Schools love Java because it's "properly" object-oriented and good for teaching concepts. But the web runs on JavaScript (or PHP depending on who you are asking). Mobile is Swift/Kotlin. Data science is Python. Nobody's building new products in Java except enterprise companies.

Teaching Java made sense in 2005. In 2025, it's questionable at best. Unless your making Minecraft plugins

**2. No web development**
The internet exists. Most software is web-based. Yet CS classes pretend the web doesn't exist. No HTML, CSS, JavaScript. No HTTP, APIs, or how browsers work. You graduate knowing how to implement a binary search tree but not how to make a button do something.

**3. Ignoring modern tools**
Professional developers use Git, package managers, linters, build tools, cloud services. These aren't mentioned in CS classes. You're supposed to pick them up on your own somehow.

The first time I saw Git in a school context was a 15-minute intro in a senior year seminar. That's it. Meanwhile every job listing says "must know Git."

**4. Testing is theoretical**
AP CS tests you with paper and pencil. You write code by hand, which literally nobody does professionally. The exam is multiple choice and written responses. No actual compiling and running code.

This creates a weird disconnect where you can get a 5 on the AP exam but not know how to set up a development environment on your own computer.

## What Schools Should Teach Instead

If I were redesigning high school CS curriculum:

**Freshman year: Foundations**

- Python basics (simpler than Java for beginners)
- Problem solving and logic
- How computers and the internet work conceptually
- Introduction to the terminal and text editors

**Sophomore year: Building Things**

- HTML, CSS, JavaScript
- Make a personal website from scratch
- Intro to Git and GitHub
- Deploy something to the internet

**Junior year: Backend & Databases**

- Node.js or Python for servers
- SQL basics
- APIs and HTTP
- Build a full-stack project (frontend + backend + database)

**Senior year: Real-World Skills**

- Choose your focus: web, mobile, data, games, etc.
- Work on a substantial project
- Learn deployment, monitoring, debugging production issues
- Understand costs, security, and trade-offs

This would produce students who can actually build things, not just pass tests.

## The Counterargument

I can hear the teachers now: "We're teaching computer science, not software engineering. Theory matters. You need fundamentals."

Fair point. Understanding how a hash map works is valuable even if you never implement one yourself. Knowing Big O helps you choose better algorithms.

But there's a balance. Current CS education is 90% theory, 10% practice. It should be the opposite, especially in high school. Teach theory through practical projects, not instead of them.

"Build a web scraper" teaches loops, string manipulation, file I/O, and HTTP requests better than "implement bubble sort" ever will. And you end up with something you can actually use.

## The Honest Take

I don't regret taking AP Computer Science. It gave me a vocabulary for talking about programming concepts. I can recognize recursion, understand when you'd use different data structures, and know what people mean by "time complexity."

But I learned way more from building projects that broke, googling error messages at midnight, and reading documentation than I ever learned in class.

If you're serious about programming, treat school as a foundation but not the curriculum. Build things outside of class. They don't have to be good. Half my projects are terrible. But you learn by doing, not by memorizing for multiple choice tests.

The real world doesn't care if you can implement quicksort from memory. It cares if you can figure out how to integrate a payment API when the documentation is unclear and the deadline is tomorrow.

Schools teach you for tests. Real programming is about solving problems nobody's solved before, or at least problems you haven't solved. That requires different skills.

## What Actually Helped Me Learn

- **YouTube tutorials** - way better than textbooks for learning syntax and seeing things work
- **Documentation** - boring but necessary, learned to read MDN and npm docs
- **Breaking and fixing things** - broke my site so many times, that's how you learn what not to do
- **GitHub repos** - reading other people's code taught me patterns and best practices
- **Stack Overflow** - every error message leads here eventually

None of this was part of any curriculum. It's just what you do when you actually try to build something.

---

_To be clear: CS teachers are doing their best with outdated curriculum requirements. This isn't their fault. The system needs to catch up with how programming actually works in 2025._

_If you're in high school and thinking about CS: take the class, but don't stop there. Build something on the side. That's where the real learning happens._
