---
layout: post
title: Setting up a website with Jekyll
subtitle: My experience using Github Pages and Jekyll to create a personal website.
cover-img: /assets/img/alaska_pano.jpg
tags: [github_pages, jekyll]
---

## Overview
I recently setup this website using Github Pages and Jekyll and since this was a totally new experience for me, I thought it would be interesting to write about my experiences and the things I have learned and still have to learn.

## Why I wanted to create a website
So far in my career I have been in individual contributor roles at companies of varying sizes but I've always had the ambition to eventually build something of my own and be in more of a consultant/ contractor/ freelance space. Until recently my digital footprint has been very small (by design) but I've realized that I need to make myself more visible and showcase my skills by getting more involved in new technologies and projects of my own. At eSpark Learning, I work with so many talented and inquisitive people who put a lot of time into developing their skills outside of work and seeing that has been a catalyst for me to do the same and write about the interesting things I'm discovering.

## Getting Started
### Trying out Jekyll
A coworker recommended Jekyll to me so the first thing I did was go to the [Jekyll site](https://jekyllrb.com/docs/) and read the documentation. Jekyll is a Ruby gem that is used for static website generating and it seemed to be a good fit for what I was looking for. I decided it would be worth giving it a try so I walked through the [Step by Step Tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/) on the website. I got the site up and running locally but I didn't want to have to run it locally on my machine to access the website so that's where I turned to Github Pages.

### Github Pages
Github Pages is great because it allows you to deploy a static website right from your repository. I can't emphasize how easy it is. I walked through the [documentation](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll) and I was able to able to get my site hosted within an hour and I didn't have to worry about running a local jekyll server. The documentation is pretty good but I will say there are some minor gaps that required a bit of Googling and trial and error. For instance, the command to create a new jekyll site in step 7 ```jekyll new --skip-bundle .``` failed for me because it did not like the ```--skip-bundle``` flag. I was able to get the jekyll installed by simply doing ```jekyll new .``` but it didn't create a Gemfile so I had to make one myself. While I was troubleshooting some of the minor issues that came up during the setup, I found [this Github issue](https://github.com/github/docs/issues/2177) really useful, as it addresses some of the things I had to work through to get Jekyll setup with Github Pages. Once I got through the documentation I had a working website that fully deployed from my main branch, the only problem was it looked like a like a high school web design project gone horribly wrong.

I'm not a web developer or a designer and while I'm not opposed to learning more about it, spending copious amounts of time writing css stylesheets and html didn't feel like a good use of my time. There's no need to reinvent the wheel when there are lots of options for importing a theme for your Jekyll site. I didn't play around with this but I did see that Github Pages allows you to [add themes](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll) so that could be something to try. The Jekyll documentation has a [list of websites](https://jekyllrb.com/docs/themes/) that allow you to browse different themes people have created, some of which are free and open source so I opted for that.

### Jekyll Themes
I went to the [Jeykll Themes](https://jekyllthemes.io/free) site which allows you to filter by free themes and I perused through them until I found one called [Beautiful Jekyll](https://jekyllthemes.io/theme/beautiful-jekyll), which seemed to fit what I was looking for. 

From there I looked through the Github repository for Beautiful Jekyll and I was impressed by how thorough the README file and comments were. I decided to fork the repository and try it out. At this point I had already installed and setup Jekyll two times now so it didn't take me long to get it working. I was so surprised how quickly and easily I was able to start personalizing the site. 

### Final Thoughts
It can be a bit challenging to make major changes to the code for the site since I don't have a ton of web experience and I didn't write most of the source code for it. Nonetheless it's certainly helping me improve my web skills and I get a good laugh at reading some of the funny comments that are in it. All credit goes to [Dean Attali](https://deanattali.com/) who is an amazing open source developer and the creator of the Beautiful Jekyll theme. If you use his Jekyll theme or any of his other open source projects, definitely send him some money on [Github](https://github.com/sponsors/daattali) or Patreon to support his work.