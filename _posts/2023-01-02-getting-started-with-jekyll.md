---
layout: post
title:  "Getting Started with Jekyll"
date:   2023-01-02 10:00:00 -0500
categories: [tutorials]
author: Your Name
---

Jekyll is a powerful static site generator that's perfect for blogs, documentation sites, and personal websites. In this tutorial, I'll walk you through the basics of setting up a Jekyll site.

## Prerequisites

- Ruby installed on your system
- Basic command line knowledge
- A GitHub account (if you want to use GitHub Pages)

## Installation

First, install the Jekyll and Bundler gems:

```bash
gem install jekyll bundler
```

## Create a New Site

To create a new Jekyll site, run:

```bash
jekyll new my-blog
cd my-blog
```

## Run Your Site Locally

Start the local development server:

```bash
bundle exec jekyll serve
```

Your site should now be running at http://localhost:4000.

## Next Steps

In future tutorials, I'll cover:
- Customizing your Jekyll theme
- Adding posts and pages
- Working with front matter and layouts
- Deploying to GitHub Pages 