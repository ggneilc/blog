---
layout: ../../layouts/BlogLayout.astro
title: 'Vim Movement Guide'
pubDate: '2023-03-14 18:21'
blurb: 'Vim shortcuts and references'
tags: ["study","linux"]
---

<!-- Use text^[link to source] to create footnotes -->
# Motions

![[Pasted image 20230314182250.png]]

some notes: 
- Motions can be combined with any number to repeat that motion that number of times (3h, 10b, 5w, etc)
- You can combine commands with motions to do that command over that motion, (and because we just learned you can add numbers to motions, you can then combine all these together) ex: y$ copies to the end of the line, '3db' will **d**elete 3 words **b**ehind the cursor.


---
# Movements to live by:

**fuck the escape key use <ctrl + \[> instead**

- typical one line movements with right hand (HJKL)
- bounce through words with the left hand (web)
- end of line with $ beginning of line with 0
- go up and down a page with 
	- <ctrl+f> for full page down
	- <ctrl+b> for full page up (think going back up)
	- <ctrl+u> for half page up (u for up)
	- <ctrl+d> for half page down (d for down)
	you should remap these last to automatically do `zz` after to center the cursor on screen so it isn't disorienting.
- <ctrl+x> to exit terminal mode
- <ctrl+w> + HJKL to move through buffers
- \* goes to the next instance of a word your cursor is on
- \# goes to the previous instance of a word your cursor is on
- / begins searching, pressing `n` goes to the next searched term and `N` to go to previous 
- `u` for undo and `ctrl+r` for redo
- `shift+g` for the end of the page
- '{' goes to next blank line, '}' goes to previous blank line
- '\[' goes to top of page ']' goes to bottom of page

---
## Not related to Motions Commands

use `space + ff` to find files
use `space + rn` for relative line numbers


**File Tree**:
- open with `ctrl + n`
- while inside you can move with HJKL
- create new files with `a`
	- you can make a directory by ending with a /: `styles/`
- copy and paste with `c` and `p`
- rename files with `r`
- focus the file tree with `space + e`

**Buffers:**
- `space + b` creates a new buffer
- `space + h` creates a new terminal 
- `tab` cycles through buffers
- `space + x` closes the buffer

**Windows**
- `ctrl + w` activates 'window mode' (wm)
- use `wm + s | v` to split the window or vertically split
- use `wm + HJKL` to move to another window
- `ctrl + q` to quit a window

## Current setup

NvChad - base config

remaps I should make:
- Capital H moves to beginning of line
- Capital L moves to the end of the line

 ---
# Vimium

this shit makes using the browser with just your keyboard pretty intuitive:

Navigation
- 'jk' moves the screen up and down
- 'ud' moves half page up and down
- 'hl' moves the screen left and right (if applicable)
- 'JK' moves between tabs
- 'HL' goes forward and backward in history
- 'f' lets you select something on the page
- 'F' open it in a new tab
- 'gi' **g**oes to the first text input (ex. youtube search bar)

Cool shit
- 'r' reloads the page
- 't' creates a new tab
- 'x' closes current tab, 'X' restores the tab
- 'o' opens URL, bookmark, or history 'O' opens it in a new tab
- 'b' open a bookmark, 'B' opens in a new tab
- '<<' moves tab to the left, '>>' moves tab to the right

## Resources

https://www.youtube.com/watch?v=w7i4amO_zaE
https://vimtricks.com/ 
