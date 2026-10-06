# Simple firefox customisation using

This repo implements some simple firefox customisation for a vertical tab
workflow using CSS (userChrome.css) and the
[Sidebery extension](https://addons.mozilla.org/en-US/firefox/addon/sidebery/)
[(GitHub)](https://github.com/mbnuqw/sidebery).

## Requirements
- Firefox (obviously)
- [Sidebery](https://addons.mozilla.org/en-US/firefox/addon/sidebery/)
- This repository

## Setup

1. In Firefox go to `about:config` and set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true`.
   This enables loading of the `userChrome.css` file used to manipulate browser
   stylesheets.
2. Locate the directory for your current user profile. `about:support` may help
   you do that. On Linux this is usually located in
   `~/.mozilla/firefox/<some-hash>.default(-release)`.
3. In your profile directory create another directory `chrome` and copy the
   `userChrome.css` file from this repo to it.
4. Restart Firefox and the CSS overrides should now be loaded.
5. Go and install Sidebery from the [addons page](https://addons.mozilla.org/en-US/firefox/addon/sidebery/).
6. Open the Sidebery settings, go to `Styles Editor` and paste the contents of
   `sidebery-styles.css` into the editor on the right.
7. In the Sidebery settings go to `General` and enable
   `Add preface to the browser window's title if Sidebery sidebar is active`
   then set your preferred preface value. The default is `[Sidebery] `; note the
   space at the end, it is required.
8. Make sure that whatever preface value you set above is also set in your
   `userChrome.css`. Whereever a `titlepreface` is matched should contain your
   preface value like so: `#main-window[titlepreface*="[Sidebery] "]`.

The sidebar should automatically follow your browser theme but your milage may
vary on that. These settings are primarily tested on Linux and without windows
decorations so people used to titlebars and buttons may feel a little alienated.

If something isn't to your liking play around with settings, most things are
commented fairly well. For example the variables `--uc-sidebar-width` and
`--uc-sidebar-hover-width` are entirely up to personal preference and heavily
depend on your setup.

## Troubleshooting

If after an update something breaks you can always inspect the browser CSS
yourself by enabling remote debugging in the developer options and starting a
debugging session on your own browser by pressing `Ctrl + Shift + Alt + I`.

Similarly there's a debugging mode for each extension you install to find any
CSS elements used in them.
