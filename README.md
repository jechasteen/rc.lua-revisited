# Awesomer rc.lua

## How to use this

When you install awesome, it will by default use the default configuration.
You can start your own configuration by installing the rc.lua file from this repo at `$HOME/.config/awesome/rc.lua` and awesome will begin to use that file instead.

## Personal Problems I have with rc.lua

1. I think that tables should have their first element on the next line

```lua
local myNextFart = butt.fart({
    length = 0.8,
    volume = 0.3,
    smell = defaults.shouldCheckPants
})
```

This is normal practice in the JS world, but it seems to be a fairly common in C and C++, too.

In all cases, a pair of curly braces with more than one item inside should always have the first brace on the initial line with the second one matching the indentation of the initial line.
In general, any parens or brackets should serve to group and separate their content visually, therefore the ending bracket should make a nice break by having its own line at the same tab level as the statement it belongs to.

This isn't just visual either, if you want to change something, you don't have to re-arrange tab levels as your editor stuggles to cope.

2. The comments are... not great.

The `{{{ ... }}}` comment containers are completely unnecessary, IMO. They only add noise. The code should delineate itself.

Some sections have prefaces, others don't even have a heading.
For example, `awful.screen.connect_for_each_screen` comes right out of the blue.
I figure this is actually a very important section, as it is where all of screen setup takes place.
Wibars, wiboxes, tags, all sorts of cool stuff happens in this function.

It would be amazing to not have to run to the docs for everything, but sometimes is will be necessary.

3. The tables `taglist_buttons` and `tasklist_buttons` are an abomination.

I can't be the only one who would prefer more lines, but better to read.
Having the functions out in no-mans-land way off to the right is a pain in the as.
Heaven forbid you want to make a change way out there, your editor will shit its pants and yours.

4. It would be nice to have some of the default settings coded in, so that I don't have to consult the manual for little things. Consider:

```lua
s.mywibox = awful.wibar({   -- Oh also mywibox = wibar???? theres a wibox widget too!!
    position = "top",
    screen = s,
    stretch = true,
})
```
I haven't added a whole lot of these, but I may add some more in the next iteration.

5. If you were to consult the documentation for some of the stuff in this file, you will end up more confused than when you started.

I know I'm harping on this section, but inside of `connect_for_each_screen` there are a number of calls to awful.widget.whatever, but if you consult the documentation, the signatures do not seem to match.

I'm not currently sure what to make of this, but I will be experimenting with these functions as they are presented in the documentation.
In other words, I want to try to 'port' the rc.lua implementations to match that of the documentation.

6. The keybinding section is hideous and disorganized.

It should be organized by group, I figure.

## The stuff that's ok

1. Functions with only one statement can be written inline.

```
{ "quit", function() awesome.quit() end }
```

2. Not all of the tables are fucked up. Some of them follow the suggestions above perfectly.

## I've done it, so what??

You may think that since I added a third to the files length (around 200 lines) that the file might be larger, but this didn't turn out to be the case.
A small portion of the changes made was to remove extraneous white space, like in places where the assignments are perfectly aligned.
I hate that anal crap, it doesn't help. At least it doesn't help me.

All we have to do to see that its better is look at the code zoomed out.
My version has a clear heirarchy and structure, you can tell just by looking at a minimap where to go in the code by the shape it makes.