---
title: It's never the right tool for the job
date: 2024-04-19T09:12:14-04:00
draft: false
---
# Introduction
I'd like to think the realm of amateurs of any hobby and profession, most newbies/novices tend to think way too much about the tools they use instead of actually trying to learn the thing they want to learn. We can see this with guitar gear-snobs who are over-zealous in what gear they use, and what gear others use. It's this obsession with finding the perfect "tone" and being able to play with minimal friction that can cause friction in their learning. The same goes with learning anything, and personally I think I am very qualified when talking about this.

Sure, I haven't actually done anything cool or noteable in my 22 years of existence. I've made mediocre YouTube content, written a couple of songs, and have been a pretty average student for most of my life, all while having the skills and passion to do great things (as does everyone!). But that passion and obsessive-nature didn't go towards learning, rather how to learn. I remember from primary to graduating secondary school that I would research what would be the "best language to learn for a native English speaker", "how to optimally learn language", "how to do X or Y in the best way possible (QUICK AND EASY!!!)."

# My configurations now
Before reading the rest of the article, I want to take some time to briefly mention why I thought all of this wasn't necessarily a massive waste of time (to cope), but also why taking the time to learn your tools isn't actually a bad thing.

I have always had the interest of "learning my tools" and I think with Linux, it gives you this unique perspective and insight as to what it is you're using and how it works. FOSS is really cool and I am really glad I adopted it for all of my academic studies. I think that the outcome has been a net positive, but the problems I had caused a lot of stress. This is because of my own mental problems, and my inability to regulate dopamine (shoutout ADHD). I'd become obsessed over the small things and get stuck in this ADHD paralysis, unable to move from my chair and do anything meaningful while also being super restless. If I were to describe what it's like to get stuck in configuration paralysis, it's almost like a state of mania. I would have trouble focussing because I treated my body like absolute dogshit, and then spiral into configuration hell trying to figure out how anything worked.

But in the end, I have a really nice setup that although I do make changes to daily, 99% of the time it's actually one of three things:

1. I am removing a neovim plugin
2. I am adding a neovim plugin
4. I am adding snippets to my LuaSnip

I like to keep a soft cap of 35 plugins on my setup which in my opinion is still a lot, but I do lazy-load the heavy ones for markdown/tex files, so as to not slow down my overall experience.

My Qtile setup is also pretty minimal at this point. I don't use any fancy background or compositor effects. My background is pure black. My bar is pure black. I have keybinds that toggle my bar along with other menu items which I could find distracting. I only use two layouts at this point, and a lot of what I do is in tmux anyways. My tmux config is also pretty small. I don't use a plugin for my status bar like in neovim. It's just simple, and I like it that way. I've reached a point where I can get done everything I need to with very minimal friction, and if there's anything that I think about adding, I write it down somewhere and save the idea for later. When I go back to it, if I find it unnecessary, I just don't do it. It's a system that's helped a lot.

# Delusion
Enough with how I am now. This is what you came here for. This is how I got to this point in the first place. I wouldn't have reached a point of zen contentment without having a phase of extreme stress/mania/delusion/obsession LMFAO.

To make a long story short, I was delusional and over-confident in my own abilities because I had researched all the "best methods to learn" without actually learning what the best method of learning was for myself. I instead subscribed to the toxic mindset of "oh yeah I could do that easily, but I just don't want to" without ever actually applying myself. I was scared of failure, and because of that fear I almost never got my foot off the ground. Now this is all to say that at the end of the day, it isn't the tools you use, but how you use the tool. This isn't a concrete black-and-white statement, since as with everything in life, there is nuance and there are exceptions. But excluding extreme circumstances in where you're in a war-torn country, or living under a bridge without any technology, or have been forced into a labour camp, you most likely have a tool for the job. If you don't, you can talk to those around you to get that tool, and you can use that to the best of your ability for basically all of beginner/intermediate phase.

# vim/neovim
## The configuring
### The beginning
I think like most novice Thinkpad + Linux enthusiasts, I stumbled upon Luke Smith's YouTube channel. Luke Smith is an interesting guy to say the least, and I sort of bit into some of his extreme views on software (more than I'd like to admit). Internally I became some sort of "pureist" was wanting to rid myself from all bloat. This obviously developed into me using the setup that I am using today, which I think is really interesting, but there was a LOT in between then and now that I had to overcome.

### Purpose
Without getting too sidetracked, the first thing I wanted to rid myself from was a cloud-based/proprietary text editor since at this point in time I had moved over to Linux. I ended up using Google Docs for the most part (which I still do use to this day for various things), but I remember watching videos on Luke flying around his text editor with something called "vim". Now before this, the only exposure I had to vim was it being made fun of on one episode of Silicon Valley, so my limited knowledge was "it was something bad". I ended up writing my own .vimrc, and continued my vim journey from there. I eventually moved over to neovim because "duh" but wanted to take on the challenge of using a completely "lua" configuration. I watched a Primeagen video on how to make one without actually understanding what the fuck I was doing, and then struggled with that for some time. I eventually had someone make fun of my neovim config (thanks mai) so I completely refactored it into something with an "init.vim" file (which I took from jvscholz) with some lua sprinkled around for plugin configuration purposes. I also switched over to lazy.nvim for my plugin management because people were moving away from packer.

### Present day
But eventually I grew tired of it. Most of the plugins I was using were designed for neovim and lua in mind, and getting my plugins to work with this init.vim was getting tiring. I also realized I was implementing a lot more lua code into my init file without realizing, using ``lua xyc`` pretty frequently. So now I have the config I have today, which is very minimal and designed to be plug-and-play on anyone's computer.

## The over complication
I omitted a lot from the story, but there was a lot of drastic change -- most of which you can find comparing my old dotfiles repository to my current. But why did I change all of this? I want you to keep in mind that while I was configuring all of this, I was still using neovim in class on both my laptop and desktop. I was playing with my config in lectures, trying to figure out the best way to shave off microseconds of friction so I could be an "elite productivity guru" that's "different from the rest because I use neovim". This ended up creating more headache, more stress, and more friction. This obsession with mine of trying to save time is something commonly seen in speedrunners, where runners were learn time-saving strategies which can either save them 10 seconds on their 2 hour run, or complete kill it 1.5 hours into it. I've always been into optimisation, but I have never had a stronger addiction to it than when I got into the neovim + tiling window manager community.

# Linux and window managers
## The beginning
Experimenting and watching videos on vim, linux, and window managers has been both a blessing and a curse for the past 2-3 years.

I started using Linux back in 2016-2017 when I was given a chromebook for highschool. I found out about using chroot to run Linux in the background, so I got started with Ubuntu 16.04LTS. After that, I used Ubuntu 14.04LTS for a Computer Hardware course the following year. That same year I daily-drove a now defunct Arch-fork called "Antergos" because I wanted to use osu! in Linux. For those who are unaware, osu! can be optimised a lot further in Linux ultimately removing hitsound latency (which is really nice). But there was one big problem: I was using an arch-based distro without actually knowing anything about arch or my system. I was still very-much in the Windows-ecosystem mindset.

## About 2 years ago
Between when I started and now, I had been unfortunately plagued with the virus known as "distro hopping" where I would switch distros trying to find "the right workspace". This is because I didn't know the difference between a "Linux Distro" and "Desktop Environments" until I installed i3 for the first time.

I wanted to get into Linux because my friend gave me his X61, so I used Mint. I was not a complete novice since I had used Linux in the past, but I was still pretty new. From there I bricked my installation due to me forcing packages which weren't supported by my kernel, so I switched to a de-snapped version of Ubuntu.

But there was still one major issue, I didn't like how the software was being packaged. Sure I liked using i3, but I knew that my window manager of choice wasn't tied to the "distro" I was using. I figured out about the arch-install script and tried it out for myself for the first time. Since getting my T460s and installing Arch + Qtile, I haven't been the same.

## Present times
I wasted a long, and I do mean a long time trying to configure my arch environment in the "best way possible" for my own needs. Whenever I'd find an issue with my config, I'd spend hours on github trying to see what other people do or if they have a solution for me. I always wanted someone else to have a solution for me, much like when I was in primary/secondary and not wanting to do my homework because "it took too much effort and I don't need to do it".

I would spend hours trying to find the best tool and tweaker for my Qtile config, and read about how to use arch linux, before coming to a big conclusion. It doesn't matter. It really doesn't matter. Who gives a shit.

I was trying to optimize my workflow so I could remove all friction from working, that I never actually did any work. I thought I was better because I had all of these cool tools and different workflows that no one around me used, but I would still get the same grades as them or worse because I was still not applying myself. I was avoiding responsibility again to protect my own sense of ego.

# Conclusion
As it stands right now, I don't really change my configs all that often in a major way. When I was really bad, I would constantly make massive changes, fundamentally altering my entire workflow. I've reached a state where I can get things done when I want to, and I can take notes the way I want to. Even if there is a little friction here and there, that's fine. Nothing in life is perfect. Your configuration will never be perfect, and that's fine. You're going to have to waste some precious seconds hitting some vim keybinds slowly that you aren't used to, and that's fine. No one can be super fast and as optimal as they want all the time. Let go of the perfection. If you find something that really makes you upset that interrupts your workflow, write it down somewhere while you're working so you don't forget, and then acknowledge it when you're done. Don't kill your flow because one small thing is causing some friction. Don't destroy your workflow to save seconds unless you really have the free time, commitment, and mental energy to do so.
