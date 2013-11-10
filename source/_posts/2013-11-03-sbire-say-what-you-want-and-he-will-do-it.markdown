---
layout: post
title: "Sbire : Say what you want and he will do it"
date: 2013-11-03 18:42
comments: true
categories:
- Sbire
---

Sbire is a simple program which enables to execute commands by analyzing your voice. In this article, you will see how to use it and how to link it with LeapMotion.
<!--more-->

Please note *I'm not a native english-speaker*. I did probably a lot of mistakes in this article. If you want to correct it, you can change the text [here](https://github.com/GCorbel/blog/tree/master/source/_posts) and do a pull request. Thanks!

How to execute commands
-----------------------
First, in a terminal, you must type `sbire start`. This will call sox to record an audio file.
After, you simply must say what command you want and it will execute it. To recognize your voice it, will send the audio file to Google voice and get the result in JSon format.
With this result, Sbire will check in a file to find the associated command. This command is executed.

When you say something like "firefox", it will simply execute the command `firefox`. For more complex sentences, Sbire enables to create a link between commands and phrases. To do this, Sbire must have a file `~/.sbire/commands.yml` like this one :

    "chromium-browser": ["open chrome", "chrome"]
    "skype": "open skype"
    "rhythmbox-client --play": "play music"
    "rhythmbox-client --pause": "stop to play music"

To ensure than Sbire is stopped, you must type `sbire stop`. It will kill all subprocesses.

Obviously, Sbire can be used with a keyboard shortcut. This will increase the use experience.

How to record in a file
-----------------------
The second option offered by Sbire is to write what you say in a file. To do this, you must type `sbire save` and say what you want. The file `~/.sbire/text` is written. To view the file as it grows, you can do `tail -f ~/.sbire/text`. When you want to stop, you must do `sbire stop`.

Install it
----------
On linux :

    sudo apt-get install sox notify-osd ruby1.9.1
    gem install sbire
    sbire install

On mac :

    brew install sox
    gem install sbire
    sbire install

On windows :

    Install ruby with [RubyInstall](http://rubyinstaller.org/)
    gem install sbire
    sbire install

How to link it with LeapMotion
------------------------------
[LeapMotion](https://www.leapmotion.com/) is a tool which enables to recognize movements. I recently contributed to [PyLeapMouse](https://github.com/openleap/PyLeapMouse). I added the possibility to link motions with commands. It reads a file called `commands.ini` to bind commands. To link LeapMotion and Sbire, you can create a file like this :

    [clockwise]
    1finger: sbire start
    2finger: sbire start
    3finger: sbire start
    4finger: sbire start
    5finger: sbire start

    [counterclockwise]
    1finger: sbire stop
    2finger: sbire stop
    3finger: sbire stop
    4finger: sbire stop
    5finger: sbire stop

This enables to start sbire, when the user do a clockwise circle, and stop sbire, when the user do a counter clockwise circle.

Contribute
----------
I'm open to any comments and suggests. Contributions are welcomed. You can submit them on [GitHub](https://github.com/GCorbel/sbire).

More informations
-----------------
For more information on installation, usage and configuration, rendez-vous on the [GitHub page of the project](https://github.com/GCorbel/sbire).

A lot more information
----------------------
If you have other questions, contact me by email, at guirec.corbel@gmail.com, or on [twitter](https://twitter.com/GuirecCorbel).
