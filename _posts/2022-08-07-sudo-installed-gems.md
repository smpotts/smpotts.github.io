---
layout: post
title: Please, don't sudo install gems
subtitle: Ruby install lessons I learned the hard way
cover-img: /assets/img/bandelier.jpeg
thumbnail-img: /assets/img/bandelier.jpeg
share-img: /assets/img/bandelier.jpeg
tags: [ruby, gems]
---

After I accepted a new job at eSpark Learning last summer, panic soon set in that I had zero Ruby on Rails experience. I turned to Udemy to find a course on building applications with Ruby on Rails. While the course spent a great deal of time covering things like data types and String methods, it completely skipped over how to install and properly setup your local Ruby environment. This led to me hacking my way through the installation. I was using the system Ruby without realizing it and I installed the gems using ```sudo```.

## Beware of 'sudo'
The ```sudo``` command is used to execute commands with elevated, superuser privileges. The sudo command gives the user unfettered access to the operating system, and there's nothing preventing you from, say, removing the entire file system on the computer. This is why it's not the default permission set on computers. With that in mind, there are still many perfectly reasonable cases to use sudo. For instance, installing software, changing the permissions or ownership of a file, removing/ uninstalling software packages. In my case, I ignorantly installed gems with sudo as a way to force the installation through instead of working through the issues I was facing. Looking back on this now I realize how dangerous this is because sudo is essentially giving the gems root permission to my machine. If I had unknowingly installed a gem with malware in it, my computer would be toast.

## Installation
### System Ruby & Homebrew
#### TL DR; don't use them
Let's walk through the installation process, and the things I've learned. The first thing I learned from having to unwind my mess, is that Macs come with Ruby pre-installed. In my opinion, that's what makes this whole process so complicated and confusing. It's not a good idea to use the pre-installed system Ruby and the version it's on is pretty out of date. At the time of writing this, the current stable version of Ruby is 3.1.2 and MacOS Monterey is on Ruby 2.6.8. Try ```ruby -v``` to check what version is actively being used.

When I was first setting up my environment I installed Ruby via Homebrew with this command: ```brew install ruby```. This had little to no effect because I ended up using a Ruby version manager (which is what you should do), so I wouldn't recommend installing with Homebrew. As a side note, if you did want to use Homebrew to install Ruby, you would need to update the ```$PATH``` to point to where Homebrew installed Ruby. The major downside with using Homebrew to install Ruby is that it will change the Ruby version when you do a ```brew update``` and you lose the ability to switch between Ruby versions.

### rbenv Setup
I decided to use ```rbenv``` as my Ruby version manager because people were saying positive things about it on Stack Overflow. Honorable mention goes to ```rvm```, which I use on my work computer, but I can't really say I have a preference or what the differences are. They both seem to work fine.

I used Homebrew to install rbenv: ```brew install rbenv```. After that I added a couple commands to my ```.zshrc``` profile file:
```
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```
This adds rbenv to the $PATH and makes rbenv load automatically upon start up. All this is great so far, but we haven't really done anything yet. If you check ```ruby -v``` it should still be pointing to the system Ruby. This is where I went wrong with my original setup.

### Where things went wrong
I thought I had installed everything I needed at this point, so I tried to run ```gem install bundler``` inside my project directory. I immediately got back this permissions issue:
```
ERROR: While executing gem ... (Gem::FilePermissionError)
You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory
```
Instead of investigating the issue further and figuring out *why* it was happening, I was eager to start my course, and I tried to force the installation with sudo. I ran the following:
```
sudo gem install bundler
```
From then on, every time I went to run a ```bundle install``` to run one of my Rails applications, it prompted me with my root password in order to install the updated gems. I simply saw this as a minor annoyance and ignored it until I need to update to Ruby 3, and I actually had to address it.

### Installing gems properly
What happened here is that I had installed rbenv, but I didn't install any Ruby versions for it to use. So when my project went to run, it was defaulting to the system Ruby in this directory: '/Library/Ruby/Gems/2.6.0', which is owned by the root user. If you sudo installed gems with the system Ruby, don't worry about trying to undo it. Abandon ship and install a version with a Ruby version manager.

To set up Ruby with rbenv, you need to install a Ruby version and then set it as the default:
```
rbenv install 3.0.2
rbenv global 3.0.2
```
If you want to learn more about rbenv, the documentation is fantastic and can be found [here](https://github.com/rbenv/rbenv). Check the Ruby version again to make sure it's now pointing to the new version installed by rbenv. Now if you run ```gem install bundler```, it should install without any permissions issues. One thing I learned after the fact is that Bundler is installed per Ruby version, so you should only need to install it once after setting up Ruby (unless you switch between versions).

Although this was a major headache that spanned several months, ultimately I'm glad it happened because it forced me to truly understand each of these steps. Now I'm well on my way to building Rails applications!







