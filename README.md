# Awesomer rc.lua

## How to use this

When you install awesome, it will often use the default configuration found at `/etc/xdg/awesome`.
You can start your own configuration by installing the rc.lua file from this repo at `~/.config/awesome/rc.lua` and awesome will begin to use that file instead.

## Personal Problems I have with rc.lua

Have a look at the [diff](https://github.com/jechasteen/rc.lua-revisited/commit/b0e22a72035e4e487320b6e4a437951fd799f40c) and maybe skip my rambling.

1. I think that tables should have their first element on the next line

```lua
local myNextFart = butt.fart({
    length = 0.8,
    volume = 0.3,
    smell = defaults.shouldCheckPants
})
```

This is common practice in the JS world, and it seems to be a fairly common in C and C++, too.

A pair of curly braces with more than one item inside should always have the first brace on the initial line with the second one matching the indentation of the initial line.
Parens or brackets should serve to group and separate their content visually, therefore the ending bracket should make a nice break by having its own line at the same tab level as the statement it belongs to.
This isn't just visual either, if you want to change something, you don't have to re-arrange tab levels as your editor stuggles to cope.

2. The comments are inconsistent

OPINION: The `{{{ ... }}}` comment containers only add noise. The code should delineate itself.

Some sections have prefaces, others don't even have a heading.
For example, `awful.screen.connect_for_each_screen` comes right out of the blue.
I figure this is actually a very important section, as it is where all of screen setup takes place.
Wibars, wiboxes, tags, all sorts of cool stuff happens in this function.

TODO: Identify locations that need *more* comments.

3. The tables `taglist_buttons` and `tasklist_buttons`

I can't be the only one who would prefer more lines, but better to read.
Having the functions out in no-mans-land is a pain in the as.
Heaven forbid you want to make a change way out there, your editor will shit its pants and yours.

4. Maybe there should be more defaults coded in 

It would be nice to have some of the default settings coded in, so that I don't have to consult the manual for little things. Consider:

```lua
s.mywibox = awful.wibar({   -- mywibox = wibar? but there's a wibox widget? my head hurts, but now's not the time
    position = "top",
    screen = s,
    stretch = true,
})
```
I haven't added a whole lot of these, but I may add some more in the next iteration.

5. If you were to consult the documentation for some of the stuff in this file, you will end up more confused than when you started.

For instance, inside of `connect_for_each_screen` there are a number of calls to awful.widget.whatever, but if you consult the documentation, the signatures do not seem to match.

I'm not currently sure what to make of this, but I will be experimenting with these functions as they are presented in the documentation.
In other words, I want to see if it is possible to 'port' the rc.lua implementations to match that of the documentation.

6. The keybinding section is hideous and disorganized.

It should be organized by group, I figure.
This has not been implemented yet.
