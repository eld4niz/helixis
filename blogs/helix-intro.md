# helix daily usage / useful tips

Rather than Vim, Neovim, or Emacs, Helix is a "post-modern" text editor. It's not as feature-rich as Vim/Neovim or Emacs, but it's a good alternative for someone who doesn't want to spend too much time configuring their editor. It's a simple and fast editor that is easy to use.

Most of the cases I use Helix with combination of Zellij. Zellij is a terminal workspace with tmux-like keybindings. As someone who doesn't like too complex configurations, Helix/Zellij combo is perfect for me. Also both of these tools written in Rust :)

In this article, I will be sharing some useful tips and tricks that I have learned while using Helix.

This article will include:
- Buffers keybindings/commands
- How does windows work in Helix
- Copying and pasting in Helix
- Searching in Helix
- Usage of Themes
- Few tips about Helix

---

## Buffers

Concepts of tabs does not exist in Helix. We use buffers instead. Buffers are opened files in the editor. We can have multiple buffers opened at the same time. We can switch between them using keybindings or commands.

We have to set in our config.toml file:
 - bufferline = "always"

### commands

If you use `!` with any closing command it will ignore the changes and closes buffer by forcing:

`:bco` or `:buffer-close-others`: 
- This will close all the buffers except one you're working with

`:bc` or `:buffer-close`: 
- It will close current buffer

`:write-buffer-close` or `:wbc`:
- Write changes to disk and closes the buffer

### keybindings

- `Space + b` - show opened buffers
- `g + p` - previous buffer
- `g + n` - next buffer

---

## Windows

Windows in Helix are similar to splits in other editors. We can have multiple windows opened at the same time. We can split the windows horizontally or vertically. We can switch between them using keybindings or commands.

You have to press `Ctrl + w` before using any window related keybindings.

### commands

- `:hsplit` - split the window horizontally
- `:hsplit-new` - split the window horizontally and open a new buffer
- `:vsplit` - split the window vertically
- `:vsplit-new` - split the window vertically and open a new buffer
- `:buffer-close` - close the buffer in the current window

### keybindings
- `Ctrl + v` - split the window vertically
- `Ctrl + s` - split the window horizontally

---
## Copy and Pasting

Copying in Helix is similar to other editors. We can use `space + y` key to copy the selected text. We can copy a single line or multiple lines.

### commands

- `:clipboard-yank` - copy the selected text
- `:clipboard-yank-join` - copy the selected text and join the lines
- `:primary-clipboard-yank` - copy the selected text using the primary clipboard
- `:clipboard-paste-after` - paste the copied text after the cursor
- `:clipboard-paste-before` - paste the copied text before the cursor
- `:primary-clipboard-paste-after` - paste the copied text using the primary clipboard after the cursor
- `:primary-clipboard-paste-before` - paste the copied text using the primary clipboard before the cursor

### keybindings

- `space + y` - copy the selected text
- `space + p` - paste the copied text after the cursor
- `space + P` - paste the copied text before the cursor

---

## Searching

Search commands all operate on the `/` register by default.

### keybindings

`/` - search for a pattern
`?` - search for a pattern in reverse
`n` - select the next search match
`N` - select the previous search match
`*` - use the current selection as the search pattern

---
## Themes

Helix has a few themes that you can use. You can set the theme in the config.toml file.

### commands

`:theme` - show the current theme
`:theme <theme-name>` - set the theme

You can also set up your favorite theme based on your preference. Check it out:

[Original Themes from Helix](https://github.com/helix-editor/helix/wiki/Themes)
[Custom theme](https://github.com/CptPotato/helix-themes)

---
## Few tips about config.toml file

### keybinding

If you want to use `/` as keybinding you have to use it inside of string as `7`. 

- Let's say you want to assign `Ctrl+"/"` to commenting in Helix, so basically in config.toml file it should look like this:

```toml
"C-7" = "toggle_comments"
```

https://github.com/helix-editor/helix/issues/3210

### finding commands or keybindings

Just by clicking `Space + ?` will show you fuzzy finder that you can find any command/keybinding with basic searching of your keyword

### cleaning your fuzzy finder

For example, let's say you're working with Django project and you have your own virtual environment. When you try to search for something in the fuzzy finder, there are lots of unnecessary files (such as binaries, lib files in the venv folder, etc.), and you basically want to clean up your fuzzy finder.

In that case, you just have to create a file named `.ignore`. It will work the same as `.gitignore`. It will ignore the files from the fuzzy finder, and your finder will be cleaner.

---
## Conclusion

Thank you for your time. Helix documentation/configuration are pretty simple and straightforward, but I wanted to share some useful tips and tricks that I have learned while using Helix.

I'm also planning to write a few more articles about Helix/Zellij, such as:

- How to set up Rust and Python LSP with Helix
- How to use Zellij with Helix

I hope you find this article helpful. If you have any questions or suggestions, feel free to reach out to me:

- [Twitter](https://twitter.com/s4movar)
- [GitHub](https://github.com/eld4niz)
