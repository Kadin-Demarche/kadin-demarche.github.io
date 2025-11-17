---
title: "Why I Built My Own Static Site Generator Instead of Using Jekyll"
date: 2025-11-20
author: "Kadin DeMarche"
tags: ["programming", "tech", "projects"]
excerpt: "Jekyll is fine. Hugo is fine. But sometimes you just want to build something yourself that works exactly how you want it to work."
---

# Why I Built My Own Static Site Generator Instead of Using Jekyll

I needed a blog. Jekyll is the obvious choice for GitHub Pages. It's mature, well-documented, and everyone uses it.

So naturally, I spent two weeks building my own static site generator instead.

This probably sounds stupid. Why reinvent the wheel when perfectly good wheels exist? But there were actual reasons, I swear.

## The Jekyll Problem

Jekyll isn't bad. It's actually pretty good at what it does. But here's what annoyed me:

**Ruby dependencies are a pain.** I don't write Ruby. I write JavaScript. Having to install Ruby, figure out gems, and debug Ruby toolchain issues just to run a blog felt wrong. Every time I switched computers or updated my system, something would break. I'd spend 20 minutes googling RVM vs rbenv issues instead of just writing.

**The plugin ecosystem is too much.** Want search? Install a plugin. Want better syntax highlighting? Plugin. Want RSS that works how you want? Plugin. Then you're managing dependencies and hoping they all work together. And half the plugins haven't been updated in 3 years. Feels like wordpress. Not like theres anything wrong with that... (theres a lot)

**GitHub Pages has limited plugin support.** You can't just use any Jekyll plugin on GitHub Pages. They have an allowlist. So you either use only blessed plugins or you build locally and push the compiled site. Which means you lose the convenience of automatic builds.

**Configuration is confusing for no reason.** The `_config.yml` file has a million options and the docs assume you already know what you're doing. Simple things like "show 10 posts per page" require understanding their pagination system and template structure.

It felt like Jekyll was designed for people who were already familiar with Jekyll. There was no simple path.

## What I Wanted

I wanted something dead simple:

- Write Markdown files
- Run one command
- Get a website

No Ruby. No complex configuration. No plugin hunting. Just Node.js (which I already use for my personal automations, article about that coming soon...) and a handful of npm packages that do one thing well.

I also wanted specific features built-in:

- Full-text search without a server
- Dark mode that respects system preferences
- Clean URLs without `.html` extensions
- Fast builds even with lots of posts
- RSS and sitemap generated automatically

These aren't exotic requirements. But getting them working in Jekyll meant navigating through the absolute hellscape of plugins, themes, and stupid config options. It felt like I was spending more time configuring something than writing.

## Building MarkSite

So I built MarkSite. Took about two weeks of evening work.

**Core tech stack:**

- Node.js (already on my machine)
- Marked for parsing Markdown
- Nunjucks for templates (like Jinja/Liquid but JavaScript)
- Highlight.js for code syntax
- Date-fns for date formatting

That's it. No heavy frameworks, no complex build pipeline.

**How it works:**

1. Read all Markdown files from `content/` folder
2. Parse frontmatter (title, date, tags)
3. Convert Markdown to HTML
4. Apply Nunjucks templates
5. Generate RSS feed, sitemap, and search index
6. Output everything to `_site/`

The whole build script is like 300 lines of JavaScript. Not complicated.

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

I wanted search, but I didn't want to run a server or use a paid service. Client-side search means generating a JSON index at build time, then using JavaScript to search it in the browser. Works instantly and costs nothing (Yay).

The search index is just an array of objects with post titles, content, and tags. Bundle it as `/search-index.json`. Load it when someone visits the search page. Simple.

**Why not use a framework like Next.js or Gatsby?**

Too heavy. I don't need React for a blog. Static HTML is fine. Those frameworks are great for apps, but for simple content sites they're overkill. Plus, longer build times and more moving parts.

**Why support dark mode?**

Because I use dark mode and it's annoying when sites don't have it. Adding it was literally just CSS custom properties and a `prefers-color-scheme` media query. Took an hour.

## What I Learned

Building your own tools teaches you way more than using existing ones. Also means that you are to blame for the issues that you encounter, I can't hide behind an excuse of terrible docs.

I learned:

- How Markdown parsers work
- How template engines render HTML
- How to structure a simple CLI tool
- How RSS feeds are formatted (they're just XML with specific tags)
- How sitemaps work for SEO
- How to build a search index from content

This stuff is useful beyond just blogs. Now when I look at other static site generators or build tools, I understand what they're doing under the hood. I'm not just cargo-culting configuration from Stack Overflow.

**The (probably?) real reason I built it:** I wanted to understand how these tools work. Reading documentation doesn't stick the same way building something does. I am a hands on kind of person so this is really great for helping me understand concepts that I otherwise fail to grasp.

## Would I Recommend This?

If you just need a blog and don't care about the internals: use Jekyll. Or Hugo. Or 11ty. They're all fine (kinda).

But if you want to learn how static sites work, building your own is worth it. The time "wasted" building MarkSite wasn't actually wasted. I understand web fundamentals better now.

Plus, now I have something I fully control. No waiting for plugin updates. No mysterious build errors. When something breaks, I know exactly where to look because I wrote it.

Its also a flex (depending on your audience).

## The ~Downside~ Darkside

MarkSite doesn't have:

- A theme ecosystem (you're on your own for design)
- Plugin support (you edit the code directly)
- A big community (it's just me so far)
- Battle-tested scaling (I have less than 10 at the time of writing)

For a personal blog, these don't matter. For a team blog or a massive site, you'd want something more mature.

But for learning and having full control? Building your own definetly wins.

---

_MarkSite is on GitHub if you want to look at the code. It's nothing terribly fancy, just a straightforward Node.js script that turns Markdown into HTML. MIT licensed. Do whatever you want with it._

_I still think Jekyll is good. I just wanted to build something myself. Sometimes that's reason enough. And Jekyll is overrated._
