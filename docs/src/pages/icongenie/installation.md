---
title: Icon Genie CLI Installation
desc: How to install the Icon Genie CLI on your development machine.
---

Make sure that you have Node >=10 and NPM >=5 installed on your machine.

You will be installing the Icon Genie CLI globally. You don't need to install it in your project folder.

```bash
# Node.js >=10 is required.

$ yarn global add @quasar/icongenie
# or
$ npm install -g @quasar/icongenie
```

This will install the `icongenie` command line tool.

## Installation tips

If you are using Yarn, make sure that the Yarn [global install location](https://yarnpkg.com/lang/en/docs/cli/global/) is in your PATH:

```bash
# in ~/.bashrc or equivalent
export PATH="$(yarn global bin):$PATH"
```

Under Windows, modify user's PATH environment variable. If you are using yarn then add `%LOCALAPPDATA%\yarn\bin`, otherwise if you're using npm then add `%APPDATA%\npm`.

## Upgrading to v2

This section applies to those that have been using Icon Genie v1 and are now upgrading to Icon Genie v2.

### NPM package name change

Version 1 was a Quasar [App Extension](/app-extensions/introduction) and so you installed it into your project folder. The new version (v2) does NOT need to be installed locally as it is installed globally. Your CI/CD will not need it as it is a one-time process and the output files (images) will be added directly to your project folder.

As a consequence, please uninstall Icon Genie v1 from your project folder:

```bash
# from your Quasar CLI project folder:
$ quasar ext remove @quasar/icon-genie
```

### Input files

With version 1 you were used to having an app-icon.png (at a fixed width and height) and an app-splashscreen.png (again, at a fixed width and height). This is no longer the case with version 2. You will now just need a png file (its name can be anything) with transparency and with minimum of 64x64 px (but the higher, the better! -- recommended size: 1024x1024) for the icon, and then another optional png (any name) for the background of the splashscreens (min 128x128 px, but recommended is 2048x2048 px).

The splashscreens work in a completely different manner too. They will get generated with the icon on top of the optional background. The size ratio of the icon to width or height (whichever is lower) can be adjusted with the CLI params (`--splashscreen-icon-ratio`). You can even tell Icon Genie that the ratio is 0 so it won't add the icon on top of the background.

### Output files

We have refined the list of icons and splashscreens that get generated to match the latest standards and to also avoid duplication. So you will notice that some of the older files don't get generated anymore and some are completely new. Icon Genie will now tell you what tags you need to add (if any) to your /src/index.template.html (you can copy paste them and replace your old ones) -- so be mindful about the list of tags.