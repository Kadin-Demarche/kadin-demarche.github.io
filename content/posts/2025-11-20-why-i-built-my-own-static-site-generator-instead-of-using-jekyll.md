---
title: "I built my own blog generator because jekyll annoyed me"
date: 2025-11-20
author: "Kadin DeMarche"
tags: ["programming", "tech", "projects"]
excerpt: "Jekyll is fine. Hugo is fine. But sometimes you just want to build something yourself that works exactly how you want it to work."
---

# I built my own blog generator because jekyll annoyed me

I needed a blog. Jekyll is the obvious choice for GitHub Pages. It's mature, well-documented, and everyone uses it. The safe choice.

So naturally, I spent two weeks building my own static site generator instead. Because of course I did. This was during a particularly bad procrastination period where I was avoiding AP Physics homework and French assignments. Building a static site generator felt more important than conjugating verbs, you know?

This probably sounds stupid. Why reinvent the wheel when perfectly good wheels exist? But there were actual reasons, I swear. It wasn't just me being difficult (though that was part of it).

## The Jekyll Problem

Jekyll isn't bad. It's actually pretty good at what it does. But here's what annoyed me:

**Ruby dependencies are a pain.** I don't write Ruby. I write JavaScript. Having to install Ruby, figure out gems, and debug Ruby toolchain issues just to run a blog felt wrong. Every time I switched computers or updated my system, something would break. I'd spend 20 minutes googling RVM vs rbenv issues instead of just writing. That's not how I want to spend my time.

**The plugin ecosystem is too much.** Want search? Install a plugin. Want better syntax highlighting? Plugin. Want RSS that works how you want? Plugin. Then you're managing dependencies and hoping they all work together. And half the plugins haven't been updated in 3 years. Feels like WordPress. Not like there's anything wrong with that... (there's a lot)

**GitHub Pages has limited plugin support.** You can't just use any Jekyll plugin on GitHub Pages. They have an allowlist. So you either use only blessed plugins or you build locally and push the compiled site. Which means you lose the convenience of automatic builds.

**Configuration is confusing for no reason.** The `_config.yml` file has a million options and the docs assume you already know what you're doing. Simple things like "show 10 posts per page" require understanding their pagination system and template structure. Why is it so complicated?

It felt like Jekyll was designed for people who were already familiar with Jekyll. There was no simple path. You either already knew it, or you spent hours figuring it out. I didn't want to spend hours.

## What I Wanted

I wanted something dead simple:

- Write Markdown files (easy)
- Run one command (simple)
- Get a website (done)

No Ruby. No complex configuration. No plugin hunting. Just Node.js (which I already use for my personal automations, article about that coming soon...) and a handful of npm packages that do one thing well. That's it.

I also wanted specific features built-in:

- Full-text search without a server
- Dark mode that respects system preferences
- Clean URLs without `.html` extensions
- Fast builds even with lots of posts
- RSS and sitemap generated automatically

These aren't exotic requirements. But getting them working in Jekyll meant navigating through the absolute hellscape of plugins, themes, and stupid config options. It felt like I was spending more time configuring something than writing. That's backwards. I want to write, not configure.

## Building MarkSite

So I built MarkSite. Took about two weeks of evening work. Not bad, honestly.

**Core tech stack (the simple version):**

- Node.js (already on my machine, no setup needed)
- Marked for parsing Markdown (does one thing, does it well)
- Nunjucks for templates (like Jinja/Liquid but JavaScript, so I understand it)
- Highlight.js for code syntax (works out of the box)
- Date-fns for date formatting (simple and reliable)

That's it. No heavy frameworks, no complex build pipeline. Just a few packages that do their job.

**How it works:**

1. Read all Markdown files from `content/` folder
2. Parse frontmatter (title, date, tags)
3. Convert Markdown to HTML
4. Apply Nunjucks templates
5. Generate RSS feed, sitemap, and search index
6. Output everything to `_site/`

The whole build script is like 300 lines of JavaScript. Not complicated. I can read it and understand it, which is more than I can say for Jekyll's internals.

**Commands:**

```bash
marksite build        # builds site
marksite serve        # runs local server
marksite new "title"  # creates new post
```

That's all I needed. Everything else is just writing Markdown.

## Technical Decisions

**Why Nunjucks over other template engines?**

It's maintained by Mozilla, has good docs, and the syntax is similar to Liquid (which Jekyll uses). So existing Jekyll theme ideas could be adapted easily. Also, it's just JavaScript, so no weird build steps.

**Why client-side search?**

I wanted search, but I didn't want to run a server or use a paid service. Client-side search means generating a JSON index at build time, then using JavaScript to search it in the browser. Works instantly and costs nothing (Yay). No server needed.

The search index is just an array of objects with post titles, content, and tags. Bundle it as `/search-index.json`. Load it when someone visits the search page. Simple. And it works.

**Why not use a framework like Next.js or Gatsby?**

Too heavy. I don't need React for a blog. Static HTML is fine. Those frameworks are great for apps, but for simple content sites they're overkill. Plus, longer build times and more moving parts. I wanted something fast and simple.

**Why support dark mode?**

Because I use dark mode and it's annoying when sites don't have it. Adding it was literally just CSS custom properties and a `prefers-color-scheme` media query. Took an hour. Easy win.

## What I Learned

Building your own tools teaches you way more than using existing ones. Also means that you are to blame for the issues that you encounter, I can't hide behind an excuse of terrible docs. When something breaks, it's my fault. Which is actually kind of freeing.

I learned:

- How Markdown parsers work
- How template engines render HTML
- How to structure a simple CLI tool
- How RSS feeds are formatted (they're just XML with specific tags)
- How sitemaps work for SEO
- How to build a search index from content

This stuff is useful beyond just blogs. Now when I look at other static site generators or build tools, I understand what they're doing under the hood. I'm not just cargo-culting configuration from Stack Overflow.

**The (probably?) real reason I built it:** I wanted to understand how these tools work. Reading documentation doesn't stick the same way building something does. I'm a hands-on kind of person so this is really great for helping me understand concepts that I otherwise fail to grasp. I learn by doing, not by reading.

## Would I Recommend This?

If you just need a blog and don't care about the internals: use Jekyll. Or Hugo. Or 11ty. They're all fine (kinda). They'll work, and you won't have to build anything.

But if you want to learn how static sites work, building your own is worth it. The time "wasted" building MarkSite wasn't actually wasted. I understand web fundamentals better now. I know how Markdown parsing works, how templates render, how RSS feeds are structured.

Plus, now I have something I fully control. No waiting for plugin updates. No mysterious build errors. When something breaks, I know exactly where to look because I wrote it. That's valuable.

It's also a flex (depending on your audience). "I built my own static site generator" sounds cooler than "I use Jekyll."

## The ~Downside~ Darkside

MarkSite doesn't have:

- A theme ecosystem (you're on your own for design)
- Plugin support (you edit the code directly)
- A big community (it's just me so far)
- Battle-tested scaling (I have less than 10 at the time of writing)

For a personal blog, these don't matter. For a team blog or a massive site, you'd want something more mature.

But for learning and having full control? Building your own definitely wins. No question.

---

_MarkSite is on GitHub if you want to look at the code. It's nothing terribly fancy, just a straightforward Node.js script that turns Markdown into HTML. MIT licensed. Do whatever you want with it. Fork it, break it, improve it._

_I still think Jekyll is good. I just wanted to build something myself. Sometimes that's reason enough. And Jekyll is overrated. There, I said it._
