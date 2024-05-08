---
title: "Neovim + LaTeX + Linguistics"
date: 2024-05-08
categories:
    - guide
tags:
    - vim
    - LaTeX
draft: true
---
_This is the first in a series of informational posts where I create technical write-ups on things I either find interesting or use on a daily basis._

# Preface
Although this is a guide on how to use and install my Neovim configuration, this isn't really an in-depth guide on how to use all the individual tools as that would take a really long time, and this already-large text would become even more overwhelming to others. There are plenty of resources online that explain how to use vimtex and vim-latex-live-preview so I will link guides throughout this post.

# Introduction
This write-up is a beginner-friendly guide to how to install and use the Neovim configuration I use for LaTeX and Linguistics course work. I am a Linguistics major (if that isn't already obvious) and I've been using vim since my second year of undergrad. My only reason being was that I switched to using a laptop that was so old that modern text-editors felt too sluggish for a lot of my needs. So with that, I used vim -- eventually switching over to Neovim.

The configuration shown here uses about ~35 plugins total for various things. I try to keep my installation on the lighter-side without too many bells and whistles to ensure smooth stable performance. I lazy-load my heavy plugins because of this.

## Short-forms I use in this article
* dir = directory/folder
* cd = change directory (go to x dir)
* nvim = Neovim/neovim
* vim = vim/nvim (i explicitly refer to nvim as the editor, and vim as both the editor and the vim-motions)

# Who this guide is for
* People who are migrating their .vimrc -> init.lua
    - I will not explain how to convert your .vimrc. This guide is for **Neovim**, not vim.
* People who already know how to use vim/nvim
* People who are familiar with how the terminal works
* People who are into writing with LaTeX
* People who are linguists/future linguists who know how to use vim
* Linguists who have their own Neovim + LaTeX setup who are looking for inspiration!


# Requirements
You need to have some level of vim knowledge. I mean it. There are a lot of people who will waste their time trying to go through the installation and setup process for the tools in this tutorial but will never use them because they don't even know how to exit vim. Vim is a skill in of itself, so if this is your first time using vim, this isn't the place to be. Please learn the basics and know how to edit your .vimrc/init.lua config before anything please.

Although this is worded as a _beginner-friendly guide_, this will be mainly targeted towards Linux/MacOS users. I don't use MacOS right now but I know it's Unix based so the file structure for the configuration and everything should work fine. I will also be assuming that you have some level of knowledge of how to use the terminal. If you know how to change directories and edit files, you're fine.

Also make sure that your Neovim version was compiled with Python3 support, since that's essential for later sections of this guide.

```bash
      /\             USER poto
     /  \              OS Arch Linux
    /\   \         KERNEL 6.8.7-arch1-1
   /      \        UPTIME 149h 6m
  /   ,,   \        SHELL bash
 /   |  |  -\        PKGS 1750
/_-''    ''-_\
```


# Organization

This is going to be organized in a few parts:
TBD

# Neovim
## Installing Neovim
As mentioned earlier, I am assuming you have some sort of idea of how to use the terminal. Open your terminal of choice and type in the following

    sudo pacman -S nvim

It should install the latest version of Neovim (which for me on Arch is 0.9.5). Now while still in your terminal, type ``nvim``. Congrats, you're greeted with nvim! That's it. You now have Neovim installed onto your system. Tutorial over! /s

If you have never configured Neovim before. It can seem very daunting. There are files everywhere and you only know how to use hjkl -- it's intimidating. I get it. We're going to work through this.

## Cloning my config

## Navigating to your config
The first thing you should do is navigate over to your ``$XDG_CONFIG_HOME``, which on most Unix systems is located at ``$HOME/.config``. If you don't have this directory (which I think is likely if you use a MacOS machine), you're going to have to make it. Make sure you're in your ``$HOME`` directory. If you don't know if you're in it or not, just type ``cd`` into your terminal and that'll take you back to it. Now type ``mkdir .config/`` while in your ``$HOME``. Next, (c)hange (d)irectories (cd[^1]) into your ``.config/`` folder by typing ``cd ~/.config/``. The ``~/`` in front of ``.config/`` is something you may have never seen before. ``~/`` is basically another way of saying ``$HOME`` when navigating. Don't worry about it too much if it seems scary. If you already have an nvim configuration but still want to try out/go through my config, click [here](https://github.com/tokisuno/nvim) to view them online. If you want to use them on a local system, make sure you're in ``~/.config/`` and there's no other nvim folder in the dir. Now, run the following: ``git clone https://github.com/tokisuno/nvim.git nvim/``. This creates a copy of my configuration and puts it onto your computer.

If the git status is making your shell slow, while in ``~/.config/nvim``, **AND MAKE SURE YOU'RE IN THERE**, type ``rm -rf .git``. This just de-initializes the folder for git version control.

[^1]: ``cd`` is how we'll be "changing directories" throughout this tutorial. It's important to note that if you have no idea what ``cd`` does, you should at least know it doesn't "change" any directory. It changes changes which directory you (the user) is in. The directory itself is the same as when you weren't ``cd``'d into it :)

# Explaining the important stuff
This section is going to cover the important files that you'll need to be somewhat familiar with to make your own changes in in the future.

## ~/.config/nvim/
The file that kick-starts this all is ``init.lua`` which is only 3 lines long.
```lua
vim.g.mapleader = " "
vim.g.maplocalleader = ","
require("lucas")
```
All what this file does is bind the two leader keys nvim needs to function, and calls this ``require()`` function to the module ``"lucas"``. What that is will be explained in just a second.

## ~/.config/nvim/lua/
There's just one folder in here called ``lucas``. This is the root folder of my nvim configuration! It may seem weird, but the reason I set it up like this was so then anyone could go through my dotfiles and have a basic understanding of what everything does without feeling too intimidated. If you have your own configuration that's in a similar style to this, all you have to do is import my config remove the ``require()`` flag for your own, and that's all!

I don't really run anything fancy in here.

## ~/.config/nvim/lua/lucas/
This is where the real configuration is.
### init.lua
All this does is load the other configuration files. The ``lazy/`` folder that's in here is automatically read by lazy.nvim when nvim is run, so that doesn't have to be called. Lazy.nvim runs through the ``lazy-config.lua/`` file, which is called on the first line. Lazy is our plugin manager, so if you're confused, that's all you need to know about it.
```lua
require('lucas.lazy-config')
require('lucas.set')
require('lucas.keymaps')
require('luasnip.loaders.from_lua').lazy_load({paths = '~/.config/nvim/lua/lucas/LuaSnip/'})
```

### set.lua
There's not a whole lot in here that needs explaining.
```lua
--- ...
--- ...
vim.cmd('syntax on')
vim.cmd('syntax enable')
vim.cmd('filetype plugin on')
--- ...
--- ...
```
Just know that these are important and shouldn't be turned off. There is more to the file as you will see by looking at it, but I think it is mostly self-explanatory. If anyone has any questions as to what things do, just hit me up on Discord and I'll be happy to help :)
```lua
local augroup = vim.api.nvim_create_augroup
local autocmd = vim.api.nvim_create_autocmd
--- ... skip skip skip
augroup('nocol', { clear = true })
autocmd("Filetype", {
  group = 'nocol',
  pattern = {"markdown", "latex"},
  command = "setlocal cc=0"
})
```
If you have used vim before and use the colorcolumn, this is an autocmd that hides it when you're in either a markdown or latex file. Really useful and has saved me a lot of time typing this in manually every time I am in a markdown/latex project :')

This is the last autocmd that I use and I think it's probably the most useful.
```lua
augroup('set_wrap', { clear = true })
autocmd('FileType', {
  group = 'set_wrap',
  pattern = {
    'gitcommit',
    'markdown',
    'text',
  },
  callback = function()
    local opts = { noremap = true, silent = true }
    vim.opt_local.spell = true
    vim.opt_local.wrap = true
    vim.api.nvim_buf_set_keymap(0, 'n', 'j', 'gj', opts)
    vim.api.nvim_buf_set_keymap(0, 'n', 'k', 'gk', opts)
  end,
})
```
I stole this from some reddit comment, but it's been a game-changer. What this does is enable "visual line-jumping". When you use nvim with word-wrapping, you'll notice that you can't go from line to line the same way that you can in a normal text document. That's because what you're seeing is the editor visually wrapping the lines for you, but in reality it's still one line. You can get around this by typing ``gk`` every time you want to go down a visual line, but that takes a lot of effort to do *every single time you want to go down one line*. This just automatically remaps ``jk`` -> ``gj gk`` every time you're in a markdown/latex environment. If you want to jump real lines though, this creates a problem. If you have a long paragraph that when word-wrapping, seems to be 5 lines tall, it's still one line. But the binds still apply, so jumping from (example) line 150 to 20 lines up won't actually be 20 lines up. It's actually 25 lines up! To get around this, I use other vim motions or toggle word-wrapping all together to move. Below are my keymaps, and you will see how I do this.


### keymaps.lua
I think this is where things get really interesting. I use which-key.nvim, which is a fork of the popular emacs plugin for nvim. This means if you're ever confused as to what a keybinding does, fear not! Which-key has a pop-up menu which comes out some time after you've hit a motion key. I've also given a description of what each bind does, so if there's a time where you're confused by what something does, which-key will show the purpose at the bottom of your screen!

These are the keys that I use to toggle certain modes/settings while I am writing. Sometimes disabling word-wrapping makes quick navigation easier, so having it bound to <leader>tw is a really comfortable and convenient keybinding for me. <leader>tf activates my "focus mode" through a plugin [true-zen.nvim](https://github.com/pocco81/true-zen.nvim).
```lua
    t = {
        name = "Toggle",
        d = {":call ToggleDeadKeys()<CR>", "Toggle Deadkeys"},
        f = {":TZAtaraxis<CR>", "Toggle focus"},
        i = {":call ToggleIPA()<CR>", "Toggle IPA"},
        t = {":call ToggleProse()<CR>", "Toggle Prose"},
        w = {":setlocal wrap!<CR>", "Toggle word-wrapping"},
    },
```

This is a Vimtex specific command that I use to count the words in my document without counting all the LaTeX jazz. It's still a rough estimate however, and I do have a word-counter integrated into my status bar, but it's still a nice bind to have to double check how I am doing.
```lua
    l = {
        name = "LaTeX",
        c = {"<cmd>VimtexCountWords<cr>", "Count words (.tex)"},
    },
```

For people that use Zotero, here's a keymap I use to find a citation. The other keymaps I use with this plugin are in their configuration file which will be shown later. How I use Zotero requires an entirely different blog post, which I will have linked [here](https://google.ca).
```lua
    f = {
      z = {":Telescope bibtex<CR>", "Find Zotero Citation", opts},
    },
```

Lastly, this is what I use for finding files in my current project directory. It may seem weird since I still use netrw to go through files and folders, but it's what I know so don't roast me too hard :')
```lua
    p = {
        name = "Files",
        b = {builtin.buffers, "View buffers"},
        g = {builtin.live_grep, "Live grep"},
        h = {builtin.help_tags, "Help tags"},
        s = {builtin.find_files, "Find files"},
        v = {"<cmd>e .<cr>", "Open Netrw"},
    },
```

## ~/.config/nvim/lua/lucas/lazy/
Here's where things get ***REALLY*** interesting. */srs*

### write.lua
This file is where I store all the plugins I use for writing. There are only three in here, but there are actually two others, one I use for my Zettelkasten and the other for citations. Both are in their own files which are to be covered later.

This is the ethereal ever-lasting vimtex plugin, a legendary plugin for vim + LaTeX and writing enthusiasts alike. I have this load only on ".tex" files since that's the only instance which this plugin works anyways. Lazy-loading this saves a lot _(a lot)_ of startup time. I use the ``-xelatex`` flag to render in XeLaTeX since it's pretty standard when writing in Humanities (at least I think). The PDF viewer I use is Zathura, hence why it's listed under multiple ``_view_`` commands. I mention this only for those who don't know what Zathura is, and had those lines confuse you.
```lua
    {'lervag/vimtex',
      ft = {"tex"},
      config = function()
        vim.g['tex_flavor'] = 'latex'
        vim.g['vimtex_compiler_latexmk_engines'] = {['_'] = '-xelatex'}
        vim.g['vimtex_view_method'] = 'zathura'
        vim.g['vimtex_view_general_viewer'] = 'zathura'
        vim.g['vimtex_view_general_options'] = '--unique file:@pdf#src@line@tex'
        vim.g['vimtex_compiler_method'] = 'latexmk'
        vim.g['vimtex_view_automatic'] = 1
      end
    },
```

This is another essential plugin. This is the plugin that you use to render your PDFs while still in nvim! This works in conjunction with vimtex and don't require any further setup.
```lua
    {'xuhdev/vim-latex-live-preview', ft = {"tex"}},
```

Have your own opinions about Luke Smith, but vimling is something I've used every chance I've gotten. The binds for this were defined above in ``keymaps.lua``, but basically what this allows for is IPA/dead-key typing in the text editor using Luke's own preferences. If you do decide to use this plugin, I recommend having the [source code](https://github.com/LukeSmithxyz/vimling) for it pulled up in another window or monitor so you know what it is you need to type to get what you want. This isn't really a plugin and more a collection of vim scripts.
```lua
    {'Lukesmithxyz/vimling', ft = {"tex", "md"}},
```
