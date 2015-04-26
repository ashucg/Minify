`Minify` for Sublime Text
=========================

Overview
--------
`Minify` for Sublime Text can create a minified version of a currently opened CSS, HTML, JavaScript or SVG file.

`Minify` generates a new file with an altered file extension such as `.min.css`, `.min.html`, `.min.js`, `.min.svg`.

Compared to other Sublime Text minifier packages `Minify` is very light: the plugin itself is less than 200 lines of Python code.
Once installed `Minify` does not need Internet access to do its job, it works offline.

`Minify` has been tested under both Sublime Text 2 and Sublime Text 3 and it should work fine on all supported platforms (Linux, Mac OS X and Windows).

`Minify` depends on other programs written in Node.js to do its job. Detailed installation instructions for those dependencies are provided below.

Which 3rd party programs are used by `Minify`
---------------------------------------------

|                | Minify | Beautify |
| -------------- |:------:|:--------:|
| **CSS**        | [clean-css](https://www.npmjs.com/package/clean-css) or [uglifycss](https://www.npmjs.com/package/uglifycss) | [js-beautify --css](https://www.npmjs.org/package/js-beautify) |
| **HTML**       | [html-minifier](https://www.npmjs.com/package/html-minifier) | [js-beautify --html](https://www.npmjs.org/package/js-beautify) |
| **JavaScript** | [uglifyjs](https://www.npmjs.com/package/uglifyjs) | [uglifyjs --beautify](https://www.npmjs.com/package/uglifyjs) |
| **SVG**        | [svgo](https://www.npmjs.com/package/svgo) | [svgo --pretty](https://www.npmjs.com/package/svgo) |

Installation in Three Easy Steps
--------------------------------

1. Install `Minify` package for Sublime Text:<br><br>
  a) Install `Minify` via [Package Control](https://packagecontrol.io/) (this is the recommended method) :<br><br>
  First install Package Control - [see installation instructions](https://packagecontrol.io/installation)<br><br>
  Then inside Sublime Text press `ctrl + shift + p` ( `super + shift + p` on Mac OS X ) and find `Package Control: Install Package` then press Enter.
  You can search for the `Minify` pacakge by entering the package name `Minify`<br><br>
  b) You can install `Minify` from GitHub directly (this is NOT recommended) :<br><br>
  _on Mac OS X:_<br><br>
  `git clone git://github.com/tssajo/Minify.git ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/Minify`<br><br>
  Note: Replace "Sublime\ Text\ 3" with "Sublime\ Text\ 2" in the above command if you are using Sublime Text 2.<br><br>
  _on Windows:_<br><br>
  `git clone git://github.com/tssajo/Minify.git %APPDATA%\Sublime Text 3\Packages\Minify`<br><br>
  Note: Replace "Sublime Text 3" with "Sublime Text 2" in the above command if you are using Sublime Text 2.

2. Install Node.js:<br><br>
  Windows and Mac OS X users should just visit [nodejs.org](https://nodejs.org/) and click on the INSTALL button,<br>
  Linux users can download pre-compiled binary files from [https://nodejs.org/download/](https://nodejs.org/download/)<br><br>
  After successful installation, please make sure that `node` is in your `PATH`, here is how to test it:<br><br>
  Open up a shell window (`Terminal` on Mac OS X, `CMD.exe` on Windows) and issue the following command:<br><br>
  `node --version`<br><br>
  You should see a version number. But if you see an error message such as `command not found` or something similar then `node` is not available via your `PATH` and you must fix this!

3. Install required Node.js CLI apps:<br><br>
  Open up a shell window (`Terminal` on Mac OS X, `CMD.exe` on Windows) and issue the following command:<br><br>
  `npm install -g clean-css uglifycss js-beautify html-minifier uglify-js svgo`<br><br>
  Notes:<br><br>
  If you are never going to work with e.g. SVG files then you can leave out `svgo` from the above command, the same applies to `uglifycss`, etc.<br><br>
  If you already have some or all of the above Node.js CLI apps installed on your system then it is recommended to update them to the latest version with the following command:<br><br>
  `npm update -g clean-css uglifycss js-beautify html-minifier uglify-js svgo`<br><br>
  Please test that the installed Node.js CLI apps are available via your `PATH`, here is how:<br><br>
  Open up a shell window (`Terminal` on Mac OS X, `CMD.exe` on Windows) and issue the following command, for example:<br><br>
  `cleancss --version`<br><br>
  You should see a version number. But if you see an error message such as `command not found` or something similar then `cleancss` is not available via your `PATH` and you must fix this!<br><br>
  You may want to do this test for all Node.js CLI apps (`cleancss`, `uglifycss`, `js-beautify`, `html-minifier`, `uglifyjs` and `svgo`).<br><br>

IMPORTANT NOTE FOR MAC OS X USERS
---------------------------------
You need to add `/usr/local/bin` directory to your system `PATH` !

Here is how to do it properly. Note: You only need to do it once.

Open up a `Terminal` and issue the following commands:

`sudo su`

(at this point you need to enter your OS X user password)

`echo "setenv PATH /usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin" >> /etc/launchd.conf`
`exit`

At this point please verify the contents of your `/etc/launchd.conf` file.
To do that, while still in `Terminal` issue the following command:

`cat /etc/launchd.conf`

You should see the following line:

`setenv PATH /usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin`

If you do, you're all set. But it is IMPORTANT to restart your computer for this change to take effect!

How to use `Minify`
-------------------
Open a `.css` or `.htm` or `.html` or `.js` or `.svg` file in your Sublime Text editor and you can

  a) use the Context Menu inside the Sublime Text editor window,

  b) access the `Minify file` or `Beautify file` commands under Tools / Minify menu in Sublime Text,

  c) use one of the following keyboard shortcuts:

  `ctrl + alt + m` ( `super + alt + m` on Mac OS X )

  This minifies the current buffer and saves the minified version into the same directory with the
  appropriate .min.css or .min.htm or .min.html or .min.js or .min.svg file extension
  then it opens the minified file in a new editor window.

  `ctrl + alt + shift + m` ( `super + alt + shift + m` on Mac OS X )

  This beautifies the current buffer and saves the beautified version into the same directory with the appropriate
  .beautified.css or .beautified.htm or .beautified.html or .beautified.js or .pretty.svg file extension
  then it opens the beautified file in a new editor tab.

License
-------
See [LICENSE.md](https://github.com/tssajo/Minify/blob/master/LICENSE.md) file for licensing information.
