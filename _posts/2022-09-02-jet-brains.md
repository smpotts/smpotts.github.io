---
layout: post
title: Jet Brains IDEs are worth a try
subtitle: Why I'm a Jet Brains fan girl, and you should be too
cover-img: /assets/img/nola.jpeg
thumbnail-img: /assets/img/nola.jpeg
share-img: /assets/img/nola.jpeg
tags: [jet_brains, ide, software_tooling]
---

I've been using [Jet Brains IDEs](https://www.jetbrains.com/) for several years now, and I evangelize them to other engineers every chance I get. Over the years I have used a large swath of their tools including: CLion, IntelliJ, PyCharm, DataGrip and RubyMine, and they consistently impress me with their great features and ease of use. Jet Brains IDEs can sometimes be a hard sell since there are free alternatives like Visual Studio Code and Sublime Text, and most of the Jet Brains IDEs require you to purchase a license (IntelliJ and PyCharm do have free community versions though). In spite of that, I still think the Jet Brains IDEs are worth the cost, and I want to highlight some of my favorite things about these tools.

## Customizations
One of my favorite things about any of the JetBrains IDEs is the level of customization you have with the UI. Users can decide between a dark or light theme and then customize the colors and effects for the different keywords in each language it supports. I like having the autonomy of setting the color scheme because it's fun, and it makes it easier to identify the different keywords in your code.
 
Another great thing about the JetBrains color schemes is that by default, the IDEs will gray out keywords that are not being used in the code, making it easier for you to catch an error or remove those pieces.

In addition to color formatting, Jet Brains IDEs also let you configure advanced formatting for each language, so your files are consistently formatted just the way you like them. It has the configuration for things like spaces and indents, wrapping and braces, blank lines, code documentation, imports, alignment and more. This is great when you are viewing or importing a messy file because you can easily reformat the code to your preferred style.

## Plugins
JetBrains tools have a plethora of plugins that you can add to the IDE to support other languages and frameworks and make your life easier. If you open a file that's in a different language like bash for instance, the IDE detects this and will suggest adding a bash plugin. The plugin will syntax highlight the file and in some cases depending on the language, it will add support to run files in different language in the IDE. I've done this with adding R to PyCharm and PyCharm installs an R Console that allows me to run R from the IDE. There are also a bunch of plugins you can add that make the coding experience easier and more pleasant. A few of my favorites are IdeaVim to add vim editing, RainbowCSV which helps you visually separate columns in a large CSV file, and Markdown which will show you how the markdown will look on an HTML page.

## Sidebar Items and UI Panels
The JetBrains IDEs have customizable tool bars on the sides, and the bottom of the UI that allow you to choose which resources you want easy access to. On the bottom toolbar, it typically has the run console, Terminal sessions, "TODO" which compiles TODO comments from the code and "Problems" which has a list of compilation errors if any, and a git UI. I love having all these things right here so that I don't have to open up a separate terminal session or go hunting for TODO comments and compilation errors. On the side tool bars, I like to have the Project file structure open, so I can look through all the files in the project, and the Pull Requests tab. You can review pull requests, view code changes in commits, and submit a review all within the Pull Requests tab in the IDE.

## File Searching
Another one of my favorite things about the JetBrains IDEs is the file searching capabilities. The IDEs allow you to quickly search for files within the project with the "shift-shift" key command, and you can narrow the scope to specific paths or object types. You can also do a grep-style search to find a phrase in files within the project with the key command "command-shift-F". I tend to use this a lot, it's a really fast and easy way to search and it gives you a preview of the search phrase within the file.

One of the other great file search features with these IDEs is how you can find usages of an object within the project by right clicking on the object and clicking "Find Usages". This open a split view at the bottom of the IDE that will give you a list of files and places where the object is used (if at all), and a preview of where that line is used in the file. This is typically pretty reliable, but it can have problems finding references to objects when you have a MVC type project where the backend is serving objects to frontend views.

## Debugging
The debugging features in the JetBrains IDEs are the least sexy, and most valuable features they offer. If you are someone like me who often works across different languages, this is great because it's setup and used roughly the same way for each language. You simply set the break points and then can iterate through the code line by line or advance to the next break point. Along the way it shows a clean UI with the stack trace on one side of the bottom of the screen and the variables and their state on the other side. I've only scratched the surface with all the ways you can use the debugger, but it's clean and intuitive setup helps me set break points and find issues quickly.

JetBrains IDEs are really great tools for developers of all different skill levels and languages. Their customizations and features are unparalleled, and you can even export your IDE settings, so they can be shared across all their products. I definitely recommend giving them a try!

Photo: The Mississippi River in New Orleans, LA