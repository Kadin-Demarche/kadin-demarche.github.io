---
title: "why I had to shut down slate (it cost too much money)"
date: 2025-11-21
author: "Kadin DeMarche"
tags: ["startups", "tech", "cost-analysis"]
excerpt: "Building a startup as a high school student sounds exciting until you see the hosting bills. Here's exactly what it cost me to run Slate, and why I had to shut it down."
---

# why I had to shut down slate (it cost too much money)

You know that feeling when you build something you're proud of, then reality hits and you realize you can't afford to keep it running? That was Slate for me. Classic high school student problem.

I spent months building a job platform that was supposed to solve LinkedIn's problems. No paywalls, no AI spam, just clean tools for finding work. Got the auth working, built a resume editor, set up the dashboard. It felt real. Like, actually real.

This was in between Scout meetings (I'm SPL of my troop), mountain bike team practices, AP Physics homework, and French class. I'm a hard procrastinator, so a lot of this got built at weird hours when I should've been doing other things. But building felt more important.

Then I looked at what it would actually cost to run. And reality hit hard.

## The Numbers Nobody Talks About

When you're starting out building web apps, everyone talks about AWS free tier and Vercel's hobby plan. What they don't mention is how fast you outgrow those. Like, really fast.

Here's what I was looking at for Slate (the reality check):

**Backend hosting (AWS):**

- EC2 t3.micro instance: ~$8/month
- RDS PostgreSQL db.t3.micro: ~$15/month
- S3 storage for resumes/files: ~$2-5/month depending on usage
- Data transfer out: another $5-10/month once you have users

**Frontend hosting (Vercel):**

- Hobby plan works until you need more than 100GB bandwidth
- Pro plan: $20/month per member
- Serverless function executions add up fast with API calls

**Total minimum monthly: ~$50-60**

That's if everything goes perfectly and you stay small. Add monitoring tools, email services, and anything beyond basic usage and you're looking at $75-100/month easy. And that's before you even have users. Once people actually use it, costs go up.

## Why $50/Month is Actually a Lot

I'm in high school. I don't have $50 a month to burn on a project no one's using yet. That's a lot of money when you're 17.

That's $600 a year. For context, that's:

- 60 hours of minimum wage work in California (that's a lot of hours)
- Two months of gas money (I drive a lot, especially to Scout stuff and mountain bike practices)
- Most of what I'd saved from working at summer camp (my actual savings)

I'm already juggling Scouts (as SPL, I have responsibilities), mountain bike team, AP Physics, and French class. Adding a $50/month expense for something that might not even work? Not happening.

The calculation was simple but depressing: if I wanted to run Slate, I needed either users paying for it (which defeats the whole free platform idea) or I needed to make money some other way to subsidize it. Maybe ads? But then it's not free anymore.

I had neither. So I shut it down.

## The Alternatives I Considered

**Free hosting options (the hunt for free stuff):**

- Heroku killed their free tier, shucks (RIP)
- Railway gives you $5 credit but that's maybe a week of runtime (not sustainable)
- Render's free tier sleeps after inactivity, so terrible UX (users hate that)
- Netlify/Vercel work for frontend but you still need backend hosting (still costs money)

**Could've used:**

- Google Sheets as a free database (actually did this initially for CampusLink, my earlier project that I'm trying to revive right now. It works but it's janky)
- Supabase free tier (generous but limited, and you'll hit limits eventually)
- PlanetScale's free tier for database (now discontinued, because of course it is)

But here's the problem: building on free tiers means you're always one policy change away from your project breaking. These companies revoke free plans all the time. You end up migrating constantly or accepting that your project has an expiration date. Big tech giveth, big tech taketh away.

## What I'd Do with a Real Budget

If I actually had, say, $200-300 to spend on getting Slate off the ground, here's what I'd do different:

**Month 1-2: Run lean**

- Vercel for frontend (free, as long as you stay under limits)
- Supabase for database + auth + storage (free tier, generous but watch those limits)
- Focus entirely on getting 50-100 beta users (probably hang up flyers and go door to door or something so I wouldn't have to pay for advertising. Old school marketing)
- Total: $0 (the dream)

**Month 3-4: Validate before scaling**

- If users stick around, upgrade Supabase: ~$25/month
- Keep Vercel free as long as possible
- Add simple analytics
- Total: ~$30/month

**Month 5-6: Scale only if there's traction**

- If 100+ active users, move to proper hosting
- AWS with proper database setup: ~$60/month
- Email service for notifications: ~$10/month
- Monitoring tools: ~$15/month
- Total: ~$85/month

The key difference: I would've spent that first $50-60 on actually proving people wanted Slate before committing to ongoing costs. Instead, I built the whole thing first, then realized I couldn't afford to let anyone use it. Classic mistake. Build first, think about costs later. Not smart.

## The Real Lesson

Slate didn't fail because of hosting costs. It failed because I built something expensive before figuring out if anyone wanted it. The costs were just the wake-up call.

The cost breakdown was just the forcing function that made me confront reality: I'd spent months building in isolation instead of talking to potential users first. The hosting bill was going to hit whether I had 0 users or 100. And I definitely wasn't going to have 100 users without running it for a while. You need users to get users, but you need money to get users, but you need users to get money...

Classic chicken-and-egg problem, except the egg costs $600 a year and I'm a brokie. Can't afford to play that game.

## What Actually Works

After shutting down Slate, I built MarkSite (the static site generator running this blog). Total hosting cost: $0. It's just static files on GitHub Pages. No servers, no databases, no ongoing costs.

The irony is that MarkSite has been more useful to me than Slate ever was. It's simpler, costs nothing, and I actually use it. Sometimes the best projects are the ones that don't require a credit card (which I don't even have, it's a debit card). Free is underrated.

Building Slate taught me to think hard about infrastructure costs before committing to an architecture. Could I have built a job platform as a static site with client-side features? Probably not the full vision. But maybe a simpler MVP that didn't need a database? Maybe start smaller?

These are questions I should've asked in week 1, not month 3 🤦‍♂️. Live and learn, I guess.

---

_$120 might not sound like a lot, but when you're 17 and that's most of your savings from working at summer camp, it hurts. My mom asked why I was spending money on "computer stuff" and I didn't have a good answer._

_On the bright side, I learned more from failing with Slate than I would've from it succeeding. That's what I tell myself anyway. Makes the $120 sting less._
