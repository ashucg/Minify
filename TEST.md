`Minify` for Sublime Text
=========================

Overview
--------
`Minify` for Sublime Text can create a minified version of a currently opened CSS, HTML, JavaScript or SVG file.

The plugin generates a new file with an altered file extension such as `.min.css`, `.min.htm` or `.min.html`, `.min.js`, `.min.svg`.

Compared to other Sublime Text minifier packages `Minify` is very light: the plugin itself is less than 170 lines of Python code.
Once installed `Minify` does not need Internet access to do its job: it works offline.

`Minify` has been tested under both Sublime Text 2 and Sublime Text 3 and it should work fine on all supported platforms (Linux, Mac OS X and Windows).

`Minify` depends on other programs written in Node.js to do its job. Detailed installation instructions for those dependencies are provided below.

Which 3rd party programs are required by `Minify`
-------------------------------------------------

|            | Minify | Beautify |
| ---------- | ------ | -------- |
| CSS        | [clean-css](https://www.npmjs.com/package/clean-css) or [uglifycss](https://www.npmjs.com/package/uglifycss) | [js-beautify](https://www.npmjs.org/package/js-beautify) |
| HTML       | [html-minifier](https://www.npmjs.com/package/html-minifier) | [html-minifier](https://www.npmjs.com/package/html-minifier) |
| JavaScript | [uglifyjs](https://www.npmjs.com/package/uglifyjs) | [uglifyjs](https://www.npmjs.com/package/uglifyjs) |
| SVG        | [svgo](https://www.npmjs.com/package/svgo) | [svgo](https://www.npmjs.com/package/svgo) |

Installation in Three Easy Steps
--------------------------------

1. Install Node.js - [see installation instructions](https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager)

  Notes:

    On Mac OS X I usually use [Homebrew](http://brew.sh/) to install Node.js: First I install Homebrew then I install Node.js with the following command: `brew install node`

    On Windows I simply download the [Windows Installer](https://nodejs.org/#download) directly from the nodejs.org web site.

    Please make sure that `node` is available in your `PATH`!

    Here is how you can test if the `node` command is available in your `PATH`:

    Open up a shell window (`Terminal` on Mac OS X, `CMD window` on Windows) then issue the following command:

    `node --version`

    If you get a version number displayed then you are in good shape. But if you get an error message such as `command not found` or something similar
    then the `node` command is not available on your system and you must fix this!

2. Install required Node.js CLI apps:

  Open up a shell window (`Terminal` on Mac OS X, `CMD window` on Windows) then issue the following command:

  `npm install -g clean-css uglifycss js-beautify html-minifier uglify-js svgo`

  Notes:

    If you are never going to work with e.g. SVG files then you can leave out `svgo` from the above command, etc.

    If you already have some or all of the above Node.js CLI apps installed on your system then you can update them to the latest version with the following command:

    `npm update -g clean-css uglifycss js-beautify html-minifier uglify-js svgo`

    Please test that the installed Node.js CLI apps are available:

    Open up a shell window (`Terminal` on Mac OS X, `CMD window` on Windows) then issue the following command, for example:

    `cleancss --version`

    If you get a version number displayed then you are in good shape. But if you get an error message such as `command not found` or something similar
    then the `cleancss` command is not available on your system and you must fix this!

    You might be able to work around path issues by specifying the full path for each Node.js CLI app in your Sublime Text editor under
    `Settings -- User` of the `Minify Package` ( `Minify.sublime-settings` ) after you have performed step 3 below.

3. Install `Minify` for Sublime Text:

  a) install `Minify` package via [Package Control](https://packagecontrol.io/) (this is the recommended method)

    https://packagecontrol.io/packages/Minify

  b) you can install `Minify` from GitHub directly (this is NOT recommended)

    on Mac OS X:

    `git clone git://github.com/tssajo/Minify.git ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/Minify`

    Note: Replace "Sublime\ Text\ 3" with "Sublime\ Text\ 2" in the above command if you are using Sublime Text 2.

    on Windows:

    `git clone git://github.com/tssajo/Minify.git %APPDATA%\Sublime Text 3\Packages\Minify`

    Note: Replace "Sublime Text 3" with "Sublime Text 2" in the above command if you are using Sublime Text 2.

AN IMPORTANT NOTE FOR MAC OS X USERS
------------------------------------
When I installed Node.js via Homebrew on a Mac I ran into the following problem:

Unfortunately, Sublime Text did not search for executable files under `/usr/local/bin` directory regardless of my system PATH settings!
It seemed that Sublime Text's Python used its own PATH settings which I could not alter... Because of this you probably need to create a symlink on your Mac like I did:

Open a `Terminal` and issue the following command:

`cd /usr/bin && sudo ln -s /usr/local/bin/node node`

The above was required for me but it was not enough!

I also had to specify the full path for each command `Minify` uses:
After installing `Minify` open its default settings in Sublime Text editor
( Preferences -> Package Settings -> Minify -> Settings -- Default ) and copy the contents of that file to the `Settings -- User` file
( Preferences -> Package Settings -> Minify -> Settings -- User ) then you can customize your `Minify` settings there.
Please do not modify `Settings -- Default` because it will be overwritten by the next release of `Minify`!

For example, to add full path to your `cleancss` command change the appropriate line inside your `Settings -- User` file to

    "cleancss_command": "/usr/local/bin/cleancss",

How to use `Minify`
-------------------
Open a `.css` or `.htm` or `.html` or `.js` or `.svg` file in your Sublime Text editor then you can

  a) use the Context Menu inside the Sublime Text editor window

  b) access the `Minify file` or `Beautify file` commands under Tools / Minify menu in Sublime Text

  c) use one of the following keyboard shortcuts:

  `ctrl + alt + m` ( `super + alt + m` on OSX ) :

  Minifies the current buffer and saves the minified version into the same directory with the
  appropriate .min.css or .min.htm or .min.html or .min.js or .min.svg file extension then it opens the minified file in a new editor window.

  `ctrl + alt + shift + m` ( `super + alt + shift + m` on OSX ) :

  Beautifies the current buffer and saves the beautified version into the same directory with the
  appropriate .beautified.css or .beautified.html or .beautified.js or .pretty.svg file extension then it opens the beautified file in a new editor window.

License
-------
See [LICENSE.md](https://github.com/tssajo/Minify/blob/master/LICENSE.md) file for licensing information.