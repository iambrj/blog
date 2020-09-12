# Optimizing the browser experience

Created: Jul 13, 2020 2:05 AM Tags: Live list

I spend a lot of time in the browser and thus I'd like to optimize my productivity there. This post lists a bunch of hacks for the same. All of these should work on Chromium \(and thus Chrome\) as it is my primary browser and I use these there \(I was a Firefox user until it started using noticeably more resources, if anybody knows how to improve Firefox's performance please [let me know](https://t.me/iambrj)\), however most of them will work on Firefox \(and other browsers\) as well. They take barely ~15 minutes to set up but have saved me a **lot** of time, so it is definitely worth investing those 15 minutes.

## Browser keyboard shortcuts

Here are my top 5 most used ones

* `Ctrl+l`: switching to url bar from content
* `Ctrl+t`: open new tab
* `Ctrl+w`: close current tab
* `Ctrt+Shift+t`: reopen last closed tab
* `Ctrl/Alt+<number>`: switch to tab

A full list can be found [here](https://support.google.com/chrome/answer/157179?hl=en)

## Search engines

If you go to

[chrome://settings/searchEngines](chrome://settings/searchEngines)

in Chromium \(

[about:preferences\#search](about:preferences#search)

in Firefox\), you can add shortcuts for search engines. For instance, I have the following set at the moment I'm writing this blog post

![/assets/chromium-searchengine.png](https://github.com/iambrj/blog/tree/61a1413c670482c081ce30d6ec550648c5523dc1/assets/chromium-searchengine.png)

For instance if I wanted to go to the Wikipedia page on Red Hot Chilli Peppers, I'd have to enter

```text
w Red Hot Chilli Peppers
```

in the url bar instead of going to Wikipedia, clicking the search bar and entering my query.

## Plugins

### Vimium

This plugin lets me use Vim bindings inside Chromium, saving me to have to move my hands from the keyboard to the mouse. It has keyboard bindings for almost everything - scrolling, navigating tabs, opening links \(in a new tab/window\)?, inserting text in forms, searching etc. Its [GitHub README](https://github.com/philc/vimium#keyboard-bindings) lists them all.

### Adblock Plus

This blocks most ads

### uBlock Origin

This allows me to enforce my own content filtering choices - I can hide things I don't want to see etc

### Refined GitHub

This improves GitHub's UI

### wikiwand

This improves Wikipedia's UI

## Misc

* As you might've noticed in the Search engines section, I have a

  `leaveAddressBar` engine. This is to switch back to the webpage from the url

  bar, without having to click or press tab multiple times \(taken from

  [here](https://superuser.com/a/324267)\).

## TODO

The following are some things I'd like to do, but haven't figured out yet. If you have a solution or any other suggestions, you can message me [here](https://t.me/iambrj) or email me [here](mailto:joshibharathiramana@gmail.com).

* Scroll through various suggestions in the search bar

  without having to move my fingers from the home row keys

**Update**: One way to get around this is to [remap](https://github.com/iambrj/dot-files/blob/master/.Xmodmap#L8) alt + hjkl to arrow keys using xmodmap on Linux

## Update 15/07/2020

A new plugin that I started using is [autocomplete](https://chrome.google.com/webstore/detail/auto-complete/aoifdlchnbljhopodkpaieedbchgjpmo). It suggests words from the dictionary while typing and uses tab complete.

