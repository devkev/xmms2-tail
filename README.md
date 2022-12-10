xmms2-tail
==========

Installation
------------

- python2
  - `sudo apt install python-xmmsclient python-gobject-2`

- python3
  - `sudo apt install python3-xmmsclient python-gi`
    - use the `xmms2-tail` from the python3 branch
    - ensure your xmmsclient python package [has been patched](https://github.com/xmms2/xmms2-devel/pull/13):
        ```diff
        diff --git a/propdict.py.orig b/propdict.py
        index 172a74d..b39b5a3 100644
        --- a/propdict.py.orig
        +++ b/propdict.py
        @@ -8,7 +8,9 @@ except NameError:
         class PropDict(dict):
             def __init__(self, srcs):
                 dict.__init__(self)
        -        self._sources = srcs
        +        self._sources = list(srcs)
        +        if len(self._sources) == 0:
        +            self._sources = ['*']
         
             def set_source_preference(self, sources):
                 """
        @@ -54,6 +56,9 @@ class PropDict(dict):
             def _set_sources(self, val):
                 if isinstance(val, basestring):
                     raise TypeError("Need a sequence of sources")
        +        val = list(val)
        +        if len(val) == 0:
        +            val = ['*']
                 for i in val:
                     if not isinstance(i, basestring):
                         raise TypeError("Sources need to be strings")
        ```

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

