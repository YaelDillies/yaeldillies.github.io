---
layout: page
title: VSCode cheatsheet
---

Some VSCode shortcuts that are particularly helpful in relation to Lean.

## Search, selection

`Ctrl + F` opens/focuses the search dialog in the focused panel.
One can first select a word to populate the search.

`Ctrl + D` after selecting some text selects the next occurrence of that text.

`Ctrl + Shift + L` does the same but selects all occurrences at once.

`Alt + Click` creates a multicursor where you press.

`Scroll click + Drag` does a rectangular selection.

## Edition

`Ctrl + Z` undoes the last action.

`Ctrl + Y`/`Ctrl + Shift + Z` redo the last undone action.

`Ctrl + C`/`Ctrl + X` copy/cut the selected text.
If no text is selected, they copy/cut the current line instead.

`Alt + Up`/`Alt + Down` move the selected lines up or down.
If no line is selected, they move the current line instead.

## Navigation

`Ctrl + P, file name, Enter` lets you jump to a file from its name without using the explorer.

`Ctrl + W` closes the current window.

## Panels

`Ctrl + Shift + Enter` opens/closes the Lean infoview.

``
Ctrl + `
`` opens/closes the integrated terminal.

`Ctrl + B` opens/closes the left panel.

## Lean commands

`Ctrl + Shift + X` restarts Lean on the current file.

`Ctrl + Shift + P`/`Ctrl + P, >` open the command palette,
from which you can access a few relevant Lean command:
* `Lean 4: Project: Fetch Mathlib Build Cache For Current Imports`:
  Fetches cache for file in focus. Only works in Mathlib (not upstream nor downstream as of now).
  Same as `lake exe cache get <filename>`.
* `Lean 4: Project: Fetch Mathlib Build Cache`:
  Fetches cache for the whole of Mathlib. Same as `lake exe cache get Mathlib`.
* `Lean 4: Server: Restart Server`:
  Restart the Lean server. Useful if you are accidentally building something you shouldn't.