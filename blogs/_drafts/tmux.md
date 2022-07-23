---
layout: post
title: TMUXnotes
date: 19/12/2021
tags: TMUX
---
**tmux and shortcuts for me to remember**

- tmux is a terminal multiplexer that allows you to open multiple windows in cli

- commands are entered with <ctrl+b> then <key>

- to create a new tmux session iuse the command 

- ``$ tmux new -s session_name``

<mark><ctrl + b> + <c></mark> create a new window with shell

<mark><ctrl + b>+<w></mark> choose a window from a list

<mark><ctrl + b>+ < 0 ></mark> switch to window 0

<mark><ctrl + b>+< %></mark> split the current pane horizontally

<mark><ctrl + b></mark> rename current pane

**other commands that are somewhat useful**

``tmux set -g mouse on`` gives mouse scrolling capability to tmux
