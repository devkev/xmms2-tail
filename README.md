xmms2-tail
==========

Installation
------------

- python2
  - `sudo apt install python-xmmsclient python-gobject-2`

- python3
  - `sudo apt install python3-xmmsclient python-gi`
    - use the `xmms2-tail` from the python3 branch

- copy files
  - `xmms2-tail` goes into `$PATH`
  - `.xmms2-tail.yaml` goes into `$HOME` and edited to taste

- i3bar (optional)
  - `i3bar-lines` and `respawn` go into `$PATH`
  - then add an i3 `bar` section into its config file something like this:

        bar {
            status_command respawn 1 xmms2-tail | i3bar-lines 
            position top
            workspace_buttons no
            binding_mode_indicator no
            bindsym button4 nop
            bindsym button5 nop
        }

