---
layout: post
title: Multi-page, single file Dash Plotly applications
subtitle: A solution for large, data intensive apps
cover-img: /assets/img/graffiti.jpg
thumbnail-img: /assets/img/graffiti.jpg
share-img: /assets/img/graffiti.jpg
tags: [tech, python, dash, plotly]
---

I have been working on a large Dash Plotly application, and it was becoming really unwieldy to manage all the code for the application in one `app.py` file. I initially tried to pull some code into a separate file containing Dash elements needed on the page, but this felt like a bad solution and it was hard to follow the flow of the code. Eventually I found [documentation](https://dash.plotly.com/urls?_gl=1*1pgjkjj*_ga*MTIzMDY3MjU0My4xNzA1NTEyMzgw*_ga_6G7EE0JNSC*MTcxMDkwNjA1Mi4zNi4xLjE3MTA5MDYxMjkuNDcuMC4w#example:-simple-multi-page-app-with-pages) in the Dash Plotly docs on how to create multi-page applications. This is a fairly straightforward way to configure different pages that are accessible from the home page when the application launches. I happily refactored all the code from my `app.py` file into separate pages based on the functionality I wanted to see in the application. Although these changes made the code easier to read, I quickly discovered new problems with this setup. 

To give a little background, the application I am building allows users to upload multiple `.json` files as input data to the application, then from there the app processes the input files, performs calculations, and displays the data in different data visualizations. The logic for these different steps exists in different files for organizational reasons, and so the pages for my multi-page Dash Plotly app, need to import other packages in the project. The problem with this kind of setup is it makes it really hard to share data between the different pages. In my example, I have a set of static events that each of the pages in the application need to be able to access and use for analysis and visualization. I tried a number of different things to make this easier including building classes in each of the pages with getter and setter methods to try to pass the events between them, and creating a separate "data container" class to handle passing the events. None of these ideas worked. Part of the issue is because the Dash Plotly app tries to load all the pages needed in the application at start up time, so when the pages are dependent on things in other files or dependent on each other, it creates some really messy dependency issues.

After spending a lot of time on the Plotly community blog and perusing the docs, I figured out a solution to this was to use multiple pages in one file, which I found in the docs [here](https://dash.plotly.com/urls?_gl=1*1pgjkjj*_ga*MTIzMDY3MjU0My4xNzA1NTEyMzgw*_ga_6G7EE0JNSC*MTcxMDkwNjA1Mi4zNi4xLjE3MTA5MDYxMjkuNDcuMC4w#multiple-pages-in-one-file). With this setup, you define the pages for the application at the top of `app.py` using `dash.register_page` like this:
```
dash.register_page("home", path='/', layout=home.layout)
dash.register_page("matches", path='/matches', layout=matches.layout)
dash.register_page("user", path='/user', layout=user.layout)
```
Then you can define the layouts for each of the pages separately and the pages can be imported in the `app.py` file. Dash treats this configuration as if these files were all in one place, so sharing data between the pages is much easier. The multi-page in one file setup is a great way to set up large, data intensive applications using Dash Plotly.
