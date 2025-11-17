---
title: "Shutting Down Slate: A Cost Breakdown"
date: 2025-11-21
author: "Kadin DeMarche"
tags: ["startups", "tech", "cost-analysis"]
excerpt: "Building a startup as a high school student sounds exciting until you see the hosting bills. Here's exactly what it cost me to run Slate, and why I had to shut it down."
---

# Shutting Down Slate: A Cost Breakdown

You know that feeling when you build something you're proud of, then reality hits and you realize you can't afford to keep it running? That was Slate for me.

I spent months building a job platform that was supposed to solve LinkedIn's problems. No paywalls, no AI spam, just clean tools for finding work. Got the auth working, built a resume editor, set up the dashboard. It felt real.

Then I looked at what it would actually cost to run.

## The Numbers Nobody Talks About

When you're starting out building web apps, everyone talks about AWS free tier and Vercel's hobby plan. What they don't mention is how fast you outgrow those.

Here's what I was looking at for Slate:

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

That's if everything goes perfectly and you stay small. Add monitoring tools, email services, and anything beyond basic usage and you're looking at $75-100/month easy.

## Why $50/Month is Actually a Lot

I'm in high school. I don't have $50 a month to burn on a project no one's using yet.

That's $600 a year. For context, that's:

- 60 hours of minimum wage work in California
- Two months of gas money
- Most of what I'd saved from working at summer camp

The calculation was simple but depressing: if I wanted to run Slate, I needed either users paying for it (which defeats the whole free platform idea) or I needed to make money some other way to subsidize it.

I had neither.

## The Alternatives I Considered

**Free hosting options:**

- Heroku killed their free tier, shucks
- Railway gives you $5 credit but that's maybe a week of runtime
- Render's free tier sleeps after inactivity, so terrible UX
- Netlify/Vercel work for frontend but you still need backend hosting

**Could've used:**

- Google Sheets as a free database (actually did this initially for CampusLink, my earlier project that I am trying to revive right now)
- Supabase free tier (generous but limited)
- PlanetScale's free tier for database (now discontinued)

But here's the problem: building on free tiers means you're always one policy change away from your project breaking. These companies revoke free plans all the time. You end up migrating constantly or accepting that your project has an expiration date. Big tech.

## What I'd Do with a Real Budget

If I actually had, say, $200-300 to spend on getting Slate off the ground, here's what I'd do different:

**Month 1-2: Run lean**

- Vercel for frontend (free)
- Supabase for database + auth + storage (free tier)
- Focus entirely on getting 50-100 beta users (probably hang up flyers and go door to door or something so I wouldnt have to pay for advertising)
- Total: $0

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

The key difference: I would've spent that first $50-60 on actually proving people wanted Slate before committing to ongoing costs. Instead, I built the whole thing first, then realized I couldn't afford to let anyone use it.

## The Real Lesson

Slate didn't fail because of hosting costs. It failed because I built something expensive before figuring out if anyone wanted it.

The cost breakdown was just the forcing function that made me confront reality: I'd spent months building in isolation instead of talking to potential users first. The hosting bill was going to hit whether I had 0 users or 100. And I definitely wasn't going to have 100 users without running it for a while.

Classic chicken-and-egg problem, except the egg costs $600 a year and I'm a brokie.

## What Actually Works

After shutting down Slate, I built MarkSite (the static site generator running this blog). Total hosting cost: $0. It's just static files on GitHub Pages.

The irony is that MarkSite has been more useful to me than Slate ever was. It's simpler, costs nothing, and I actually use it. Sometimes the best projects are the ones that don't require a credit card (which I dont even have, its a debit card).

Building Slate taught me to think hard about infrastructure costs before committing to an architecture. Could I have built a job platform as a static site with client-side features? Probably not the full vision. But maybe a simpler MVP that didn't need a database?

These are questions I should've asked in week 1, not month 3 🤦‍♂️.

---

_If you're a student trying to build something: start with the cheapest possible version. Free hosting exists for a reason. Don't optimize for scale when you have zero users. I learned this the expensive way._

_Total sunk cost on Slate: ~$120 in hosting while building + testing, plus 3 months of evenings and weekends. At least I got a blog post out of it._
