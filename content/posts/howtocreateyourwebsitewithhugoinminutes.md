---
title: "How I created my own website and deployed it for free in a matter of hours"
date: 2022-07-02T19:53:51+02:00
draft: false
tags: ["Hugo", "Web-development"]
---
> Disclaimer: This is a tutorial to create a simple personal website with minimal work and effort but still highly configurable and easy to maintain. If you're looking for a more complex setup with more functionality I suggest you look for other resources in those topics.

## Table of contents

- [Table of contents](#table-of-contents)
- [Introduction](#introduction)
  - [My use case](#my-use-case)
  - [Technical requirements](#technical-requirements)
- [Hugo](#hugo)

## Introduction

I have always wanted to create a website for my own personal use. To show my portfolio, have my socials and share things that I found interesting or my own tutorials even. But I have never gotten around to do it because it just seems like a big hustle to do it.
There are lots of decissions to make:

- What kind of technology should I use to build? SPA (single page app), SSG (server side rendered) or SSR (server side rendered)?
- Where should I host my website? Is it expensive?
- Do I need to know how to code? Or design? CSS? HTML? Javascript?
- Where do I get a domain name? Do I even need one? I have a domain name already but I don't know how to use it.

I had all these questions that made something that in principle seemed simple but ends up feeling very overwhelming, and makes you not want to do it.

### My use case

What I always do in these situations is define the problem, hence I listed what I was going to use this site for:

- Have my socials (Twitter, Facebook, Instagram, LinkedIn, GitHub, etc.).
- Have a small bio explaining who I am, kind of a introductory text of me for anyone that searches me on the internet.
- Publish articles quickly.
- Being able to categorize archive, draft and search these articles/posts.

### Technical requirements

So with this small list of use cases in mind the next step I did was to define the technical requirements:

- I don't want to deal with HTML and CSS. I know how to use them to some extent but I think just writing the content is already a big enough task.
- I would like to write documents in [Markdown](https://www.markdownguide.org/), since I use [Obsidian](https://obsidian.md/) and [Notion](https://notion.so) for taking notes, and they use this format it seems like a good idea to keep using it. Also it is extremely easy to learn, use and has the features I am looking for, like:
  - A standardized format: # = H1 ## = H2, etc. > for blockquotes, etc. [Here you can check out the syntax](https://www.markdownguide.org/basic-syntax/).
  - No tags (god I hate html and xml tags <href ... > and the sort I find them antiquated and annoying for wrinting purposes)
  - Image embedding.
  - Inline HTML, useful for things such as iframes(youtube embedded videos i.e) or to do things that markdown itself doesn't support, which are few but exist.
  - Code block support, since I will post some coding tutorials.
- Preset styles and themes, I don't want to deal with the design, there are people out there who have much better taste and artistic skills than me, I just want to focus on the content.
- Dark theme: for the love of god I die inside when a website is white theme only.
- Easily deployable, I want the code/content of the website saved in a repository in Github, write the articles **locally** in my machine, push the changes to the remote repository on Github and the website to pick up on these changes inside the repository and update accordingly. This also allows me to revert changes easily and work in any of my machines, or even using even [Github Codespaces](https://github.com/features/codespaces) if I needed to make a quick edit.
- Extensible in case that in the future I want to add functionlity to it. This includes:
  - Javascript support: being able to write static content in Markdwon is cool and all but it has limitations, being able to code in JS can be very useful.
- I want a static site with as little JavaScript as possible, with fast loading times. I think SPA's make sense for some type of website/applications, but for my use case it would be quite stupid to use an SPA framework like Angular for example, like we say in Spain: "It would be killing flies with cannons".

So I went and looked around online to see what technologies satisfied the requirements and I stumbled across [**Hugo**](https://gohugo.io/).

## Hugo

As described in their [**website**](https://gohugo.io/):
{{< quote author="Hugo Project" source="Hugo's official website" url="https://gohugo.io">}}
Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again.
{{< /quote >}}
{{< quote author="Hugo Project" source="Hugo's official website" url="https://gohugo.io">}}
The world’s fastest framework for building websites, Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.{{< /quote >}}

So Hugo is a web framework, this means that it is a piece of software that provides a specific way to build and deploy websites, alongside the tools needed to do so. It is very simple to use, the documentation around it is great and it has a lot of functionality baked in.

The rundown of how it works. Yow download Hugo, create a project, choose an already created theme or you can build your own, configure the theme and some Hugo options, execute a Hugo command to launch a local server to test and preview stuff while you write your content in markdown, once you're done you execute another command to generate the static website(HTML,CSS, etc.) and deploy it wherever you want.

Quite simple in my opinion. Pretty much everything is handled for you.

So once I saw it could do pretty much all I wanted, I started reading the [documentation](https://gohugo.io/documentation/). Nah just kidding hahaha I went ahead to the [getting-started/quickstart](https://gohugo.io/getting-started/quick-start/) page and followed the steps.

> Note: I used a Mac but it pretty much works the same on other OS's except for the installation part.
> I use Visual Studio Code as my tool for this sort of things, [here](/posts/vscodetheultimatetool) is another article of mine explaining VSCode, how it works, my setup extensions, etc.

Go ahead and pull up a terminal, first we need to download Hugo, if you're on MacOS use [brew](https://brew.sh), the command is: `brew install hugo`.
Next navigate to the directory where you want have the project, and type `hugo new site <name of your project>`. This will create a directory inside your current one, go into it.
Next step will be to choose a theme and configure it. You can check out available themes [here](), I decided to go with [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) by Cai Jimmy. This is what it can look like using it.

![Theme example website](images/howtocreateyourwebsite/hugo_theme_stack_web.png)

[Here](https://demo.stack.jimmycai.com/) is the example Hugo website of the picture above built using this theme, as you can see.
In order to use it or any other theme use the following command inside the site folder `git submodule add https://github.com/CaiJimmy/hugo-theme-stack.git themes/hugo-theme-stack && echo theme = \"hugo-theme-stack\" >> config.toml`
This will download the theme from Github and append the theme attribute inside the confi.toml file, and set it to the hugo-theme-stack so hugo can read it and know to use it.
