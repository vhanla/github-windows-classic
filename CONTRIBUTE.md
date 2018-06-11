# HOW TO CONTRIBUTE

## Development Setup

The development of this custom userstyle is made easy using the following tools:

## Requirements

- Visual Studio Code

  It requires the following extensions:
  - [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass)
  - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) (Live Sass Compiler installs)
  - Optionally you could use [Easy Sass](https://marketplace.visualstudio.com/items?itemName=spook.easysass) instead of Live Sass Compiler

- Firefox
  - Disable [CSP](#csp) to load your local user style.
  It also requires the following add-ons:
  - [Super CSS Inject](https://addons.mozilla.org/en-US/firefox/addon/super-css-inject/?src=userprofile)
  - [Live Reload](https://addons.mozilla.org/en-US/firefox/addon/live-reload/?src=userprofile)


## <a name="csp">Disabling CSP since GitHub uses that policy</a>
***NOTICE*** *This might not be necessary, if developer tools console doesn't complain about CSP on Github.com*

Visit `about:config`
 Then disable CSP, i.e. `security.csp.enable = false`

**REMEMBER** to enable it back when you're done.

## Setup Live Reload for local SSL

Execute `./genlocalssl.sh` from localssl directory, or just use the provided self signed files already there.

.vscode/settings.json already have settings that you might need to modify.

On Windows you have to replace relative path for certificate files to full path (e.g. c:/myproject/server.crt)

FireFox will warn you when accessing the site served by Live Reload, press advanced and add it as temporary exception, or if you like add it permanently.

## Watch Sass

You also need to launch Watch Sass from status bar in VSCode, it will compile the sass files.

## Optional (Easy Sass)

It seems that this extension is better for the following reasons:
- It offers a command to compile all files
- It allows to exclude files to compile

So you can set a [macro](https://marketplace.visualstudio.com/items?itemName=geddski.macros) to trigger after saving any .scss file, and it will compile the `main.scss` and `userstyle.scss` files for our specific project.

To set that macro, install that macro extension, and add a custom keybinding (F1, then write Open Keyboard Shorcuts File) and add the following:

```json
{
  "key": "ctrl+s",
  "command": "macros.scss",
  "when": "editorTextFocus && editorLangId == 'scss'"
}
```
So each, time you save it will trigger the macro, which is already set up on .vscode/settings.json file. You can always avoid that macro extension and directly call the `easysass.compileAll` command instead of `macros.scss` in the `command` section in the keybinding file.

## How to sync Live Reload and Github site?

Open **Super CSS Inject** preferences from Add-Ons page (Ctrl+Shift+A) and add the full URL path to the compiled main.css file.

e.g. https://127.0.0.1:5500/dist/main.css

Click **Live Reload** add-on icon and Create a new reload rule.
Fill the inputs.
Title, whatever your want.
Host Url: https://github.com/*
Source File URLs:
https://127.0.0.1:5500/dist/main.css

Bare in mind, port must match with whatever VSCode's Live Reload assigned you.
Use the other default settings and save.

Finally, visit GitHub website and enable **Super CSS Inject**. It will add the main.css URL which **Live Reload** (the add-on) will start detecting changes.

## Finally

You can modify the SCSS files, update `main.scss` file and **Watch Sass** will recompile it. Live Reload (the add-on) will detect the changes and reload it on the GitHub's page. And if you wish, make a PR.



