### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Vim MODES : State Transition Diagram
![vim_new](https://user-images.githubusercontent.com/89788120/187350576-25d3425b-49b3-4365-8313-7d52bfab030d.png)

### Commands

- :q to quit (short for :quit)
- :q! to quit without saving (short for :quit!)
- :wq to write and quit
- :wq! to write and quit even if file has only read permission (if file does not have write permission: force write)
- :x to write and quit (similar to :wq, but only write if there are changes)
- :exit to write and exit (same as :x)
- :qa to quit all (short for :quitall)
- :cq to quit without saving and make Vim return non-zero error (i.e. exit with error)

### Insert Mode

- i: go to INSERT in the place of the cursor
- I: go to INSERT mode at the beginning of the line
- a: append after the cursor
- A: append at the end of line
- o: open a new line below the current line
- O: open a new line in the place of the current line

Vim Cheatsheet https://testclub.hashnode.dev/vim-cheatsheet#heading-startend-of-line-and-file
