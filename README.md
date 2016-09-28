ssh-askpass
===========

ssh-askpass for OS X/macOS. Works in (at least) 10.7+ (including Sierra)

Used to accept (or deny) the use of the private key(s) added to the SSH authentication agent with `ssh-add -c`.

![Screenshot](https://github.com/theseal/ssh-askpass/raw/master/sample/ssh-askpass.png)

**If you’re having trouble with ssh-askpass after OS upgrade, please follow the installation steps again.**

## Installation

### [Homebrew](http://brew.sh/)
* Run:

    ```
    $ brew tap theseal/ssh-askpass
    $ brew install ssh-askpass
    ```
* Follow caveats

### Without Homebrew

#### OS X Pre 10.11
```
$ sudo ln -s $PWD/ssh-askpass /usr/libexec/ssh-askpass
```
#### OS X 10.11+

* If you have XQuartz (http://www.xquartz.org/) or are willing to get it:
    * Make sure that the latest XQuartz is installed. (eg. brew cask install xquartz)
    * Run:

    ```
    $ sudo ln -s /usr/local/bin/ssh-askpass /usr/X11R6/bin/ssh-askpass
    ```
* Else:
    * [Disable SIP (rootless)](http://www.imore.com/el-capitan-system-integrity-protection-helps-keep-malware-away)
    * Run:

    ```
    $ sudo mkdir -p /usr/X11R6/bin
    $ sudo ln -s $PWD/ssh-askpass /usr/X11R6/bin/ssh-askpass
    ```
    * [Enable SIP (rootless)](http://www.imore.com/el-capitan-system-integrity-protection-helps-keep-malware-away)

## Enabling keyboard navigation
For security reasons ssh-askpass defaults to cancel since it's too easy to
press spacebar and accept a connection or other actions which might use
ssh-keys. To make it easier to press `OK`:

* Go to `System Preferences` and then `Keyboard`.

#### OS X Pre 10.11
* Under the `Keyboard` tab, click on `All controls`.

#### OS X 10.11+
* Under the `Shortcuts` tab, click on `All controls`.

Now you can press ⇥+spacebar to press `OK`.

## License
ISC license

## Contributors
* [theseal](https://github.com/theseal)
* [simmel](https://github.com/simmel)
