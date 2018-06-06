# HOW TO CONTRIBUTE

## Development Setup

The development of this custom userstyle is made easy using the following tools:

## Requirements

- Visual Studio Code

  It requires the following extensions:
  - [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass)
  - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) (Live Sass Compiler installs)
- Firefox
  - Disable [CSP](#csp) to load your local user style.
  It also requires the following add-ons:
  - [Super CSS Inject](https://addons.mozilla.org/en-US/firefox/addon/super-css-inject/?src=userprofile)
  - [Live Reload](https://addons.mozilla.org/en-US/firefox/addon/live-reload/?src=userprofile)


## <a name="csp">Disabling CSP since GitHub uses that policy</a>

Visit `about:config`
 Then disable CSP, i.e. `security.csp.enable = false`

**REMEMBER** to enable it back when you're done.

## Setup Live Reload for local SSL

Execute `./genlocalssl.sh` from localssl directory, or just use the provided self signed files already there.

.vscode/settings.json already have settings that you might want to modify.

FireFox will warn you when accessing the site served by Live Reload, press advanced and add it as temporary exception, or if you like add it permanently.

## Watch Sass

You also need to launch Watch Sass from status bar in VSCode, it will compile the sass files.

## How to sync Live Reload and Github site?

Open **Super CSS Inject** preferences from Add-Ons page (Ctrl+Shift+A) and add the full URL path to the compiled main.css file.

e.g. https://127.0.0.1:5500/main.css

Click **Live Reload** add-on icon and Create a new reload rule.
Fill the inputs.
Title, whatever your want.
Host Url: https://github.com/*
Source File URLs:
https://127.0.0.1:5500/main.css

Bare in mind, port must match with whatever VSCode's Live Reload assigned you.
Use the other default settings and save.

Finally, visit GitHub website and enable **Super CSS Inject**. It will add the main.css URL which **Live Reload** (the add-on) will start detecting changes.

## Finally

You can modify the SCSS files, update `main.scss` file and **Watch Sass** will recompile it. Live Reload (the add-on) will detect the changes and reload it on the GitHub's page.



