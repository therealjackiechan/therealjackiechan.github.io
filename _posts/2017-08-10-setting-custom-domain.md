---
layout: post
title: "Setting a NameSilo Custom Domain to a Github Pages Site"
date: 2017-08-10
tags:
- GitHub Pages
- Website Building
---

When I was setting up this website, I was having a hard time finding resources to walk me through how to connect my NameSilo custom domain to my GitHub Pages website. Instead of the default https://byjackiechan.github.io for GitHub Pages, I wanted my website to be accessed through www.byjackiechan.com. 

GitHub Pages has their own <a href="https://help.github.com/articles/using-a-custom-domain-with-github-pages/">instructions</a> on how to achieve this, but it wasn't specific enough for me. I stumbled onto a helpful <a href="https://www.chenhuijing.com/blog/setting-up-custom-domain-github-pages/">post by Chen Hui Jing</a>. She explained the basics of needing to connect my domain to GitHub's servers through specific IP addresses to get it to work. Hui Jing ended up connecting NameSilo to GitHub Pages through <a href="https://www.cloudflare.com/">Cloudfare</a>. Researching it again to write this post, I'm not sure why I didn't go that route since it's a good idea to secure your website and personal information.  

I must've wanted to get a working prototype before extending and, after some trial and error, figured out how to directly link them. I'm sharing the steps I took in hopes that it'll help someone else out or, very likely, me in the future. These instructions should work with any domain name registrar and hosting site with minor modifications.

Instructions

1) Log in to Namesilo.

2) Click on "Manage My Domains" at the top or "domain manager" on the right of the page.

<img src="/images/2017-08-10-domain-manager.jpg" alt="Domain manager link locations on login website page"/>

3) Click the blue icon, representing "Manage DNS for this domain," for the domain you want.

4) Scroll down and find the "Github" template.

5) Click apply template.

6) Make sure the number and details of the existing resource records is exactly the same as that in the following image:

If there's extraneous records, remove the record by clicking the delete icon.

If there's missing records, fill out the "Add/Edit a Resource Record" section and then click submit. 

Note: Each resource record has a TTL (time to live) value that usually defaults to 7207 seconds (2 hours), but it can be set to anything between 3600-2592000. My records have different TTL values because of the GitHub template.     

7) In your main GitHub Pages directory, add a file titled CNAME without any file extension. Save your CNAME file with your custom domain URL as the only text.

You're done! After implementing, it takes around 15 minutes to 2 hours for your DNS configuration to update. Also, the linking won't show up if your website was cached before the update, so make sure to clear your browser cache to view it properly! 