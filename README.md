[![Build Status](https://travis-ci.org/aronwoost/sublime-expand-region.png?branch=master)](https://travis-ci.org/aronwoost/sublime-expand-region)

# ExpandRegion for Sublime Text

### Like "Expand Selection to Scope". But better!

ExpandRegion works a bit like the build in "Expand Selection to Scope", however it does not depend on Scopes (Scopes are used by ST to "understand" code, i.e. for syntax highlighting). Therefore selection expansion can be more granular and customizable.

It works similar to ExpandRegion for Emacs and "Structural Selection" (Control-W) in the JetBrains IDE's (i.e. IntelliJ IDEA).

## Prereleases

Pre-releases help us to test new features and improve the stability of releases. You can benefit the newest features and help us testing them. Just open *Preferences > Package Settings > Package Control > Settings - User* and insert at a reasonable (correct JSON syntax) position:

``` js
    "install_prereleases": ["ExpandRegion"],
```

If you also use pre-releases of other packages just add them comma separated into the list.


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
   wait few seconds until the installation finishes up
1. Now,
   Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Go to the menu **`Tools -> Command Palette...
   (Ctrl+Shift+P)`**
1. Type **`Preferences:
   Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   find the following setting on your **`Package Control.sublime-settings`** file:
   ```js
       "channels":
       [
           "https://packagecontrol.io/channel_v3.json",
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
       ],
   ```
1. And,
   change it to the following, i.e.,
   put the **`https://raw.githubusercontent...`** line as first:
   ```js
       "channels":
       [
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
           "https://packagecontrol.io/channel_v3.json",
       ],
   ```
   * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
     you will not install this forked version of the package,
     but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
   go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
search for **`ExpandRegion`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


## Example

### JavaScript (should also work for other c'ish languages like Java).

![](http://aronwoost.github.io/expand-region.gif)

1. Expand selection to word
2. Expand selection to quotes (content only)
3. Expand selection to quotes (with quotes)
4. Expand selection to square braces
5. Expand selection to expression
6. Expand selection to content of braces (all arguments in this case)
7. Expand selection to line
8. Expand selection to function body (w/o curly brace)
9. Expand selection to function body (with curly brace)

and so on...

### Python

![](https://cloud.githubusercontent.com/assets/12573621/11763466/a55ccc34-a10b-11e5-92e8-71c5a827db2c.gif)

Behaves similar to JavaScript, but also depends on indentation:

1. Expand selection to word
2. Expand selection to parentheses (content only)
3. Expand selection to parentheses (with parentheses)
4. Expand selection to function call
5. Expand selection to line (w/o indent)
6. Expand selection to indentation
7. Expand selection to block start before indentation
8. Expand selection to indentation
9. Expand selection to block start before indentation
10. Expand selection to indentation
11. Expand selection to block start before indentation

and so on...

### HTML

![](http://aronwoost.github.io/expand-to-html.gif)

1. Expand selection to word
2. Expand selection to quotes (content only)
3. Expand selection to quotes (with quotes)
4. Expand selection to complete self closing tag
5. Expand selection to parent node content
6. Expand selection to complete node
7. Expand selection to parent node content

and so on...

### LaTeX (thx [r-stein](https://github.com/r-stein))

![](https://cloud.githubusercontent.com/assets/12573621/11544524/994770b4-9942-11e5-9ffc-9819d50048b6.gif)

1. Expand selection to word
2. Expand selection to command
3. Expand selection to command arguments
4. Expand selection to brackets (content only)
5. Expand selection to brackets (with brackets)
6. Expand selection to surrounding command
7. Expand selection to surrounding environment (content only)
8. Expand selection to surrounding environment (whole)
9. Expand selection to surrounding environment (content only)
10. Expand selection to surrounding environment (whole)

and so on...


## Using

- Set a shortcut.
  Open "Key Bindings - User" and add to following line:
``` js
{ "keys": ["super+shift+space"], "command": "expand_region" },
{
  "keys": ["super+u"],
  "command": "expand_region",
  "args": {"undo": true},
  "context": [{ "key": "expand_region_soft_undo" }]
},
```
Note: third party plugins can not properly hook into the history. So soft-undo in basically only a undo expand selection. Soft-redo will not work.


## Develop

## Background

This plugin is inspired by the amazing [expand-region for Emacs](https://github.com/magnars/expand-region.el).

Here a video showing this feature (in Emacs):

[![](http://img.youtube.com/vi/_RvHz3vJ3kA/0.jpg)](http://www.youtube.com/watch?v=_RvHz3vJ3kA?feature=player_embedded&v=M)

Read more:
[Extend Selection by Semantic Unit](http://ergoemacs.org/emacs/syntax_tree_walk.html)

## License

MIT
