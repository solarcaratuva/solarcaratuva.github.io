# Solar Car Wiki Source Code

This repo contains the source code from which the wiki is generated.

**[https://solarcaratuva.github.io/](https://solarcaratuva.github.io/)**

## Getting started

Before making your first changes, please contact the Embedded Lead. Provide your GitHub username, so you can be given editing rights. <br>

- A folder will be created for your subteam. Put ALL your content in this folder; this is to ensure that the source code for this wiki remains organized. 
    - It is recommended to put any external resources, like PDFs, in the team Google Drive folder and link to them in your pages, rather than putting those files in this repo.
- A blank landing page will also be created for your subteam, all pages you create should have this page as their 'parent' (described below). 

## Prerequisites 
**If you already understand Git** then it is recommended to clone this repo and edit it locally. You can use VSCode to edit / add content, and use the `Markdown Preview Enhanced` extension to view the formatted Markdown before committing it.

**If you don't understand or know about Git** then it is recommended that you add and edit content entirely through the GitHub website. [Here is a guide](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files).

## Creating Pages

All pages must begin with a metadata block *like below*, which tells the page how it falls in the page hierarchy, and isn't visible.

```
---
title: Onboarding
nav_order: 3
parent: Embedded
has_children: false
---
```

Every page must have these attributes. 
- `title` is the title the page will have in the sidebar menu. 
- `nav_order` describes the order pages in the sidebar menu appear. 
- `parent` declares which page is above this one in the hierarchy, and should always be the title of your subteam's landing page (which is your subteam name).
    - The only exception is that your subteam's landing page will not have a `parent` attribute. 
- `has_children` declares if any other pages have this page as their parent. This will probably be `false` for all pages you create. 

Besides that, the rest of the page is described in standard markdown that will be visible. <br>
For help writing with markdown, see:
1. [This guide](https://www.markdownguide.org/)
2. [Documentation for the Jekyll theme this wiki is made from](https://just-the-docs.github.io/just-the-docs/)
3. ChatGPT

It is recommended that you use the *Embedded* section of the wiki as a guide. You can view the source markdown code that makes the pages and compare it to how the actual pages look on the website.

## Saving Pages and Updating the Website

After you *commit* and *push* your changes / additions, GitHub will automatically rebuild the website. Rebuilding the website takes around a minute. Make sure to refresh the wiki website if you leave it open while GitHub is rebuilding the site. 

## Questions

If you have questions, reach out to the Embedded lead.
