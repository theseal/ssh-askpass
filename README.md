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

#### Pre 10.11
```
$ sudo ln -s $PWD/ssh-askpass /usr/libexec/ssh-askpass
```
#### 10.11+

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
* Without SIP:

    ```
    sudo tee /Library/LaunchAgents/com.openssh.ssh-agent-custom.plist <<EOF
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
            <key>Label</key>
            <string>com.openssh.ssh-agent-custom</string>
            <key>ProgramArguments</key>
            <array>
                    <string>/usr/bin/ssh-agent</string>
                    <string>-l</string>
            </array>
            <key>EnvironmentVariables</key>
            <dict>
                    <key>SSH_ASKPASS</key>
                    <string>/usr/local/bin/ssh-askpass</string>
                    <key>DISPLAY</key>
                    <string>0</string>
            </dict>
            <key>Sockets</key>
            <dict>
                    <key>Listeners</key>
                    <dict>
                            <key>SecureSocketWithKey</key>
                            <string>SSH_AUTH_SOCK</string>
                    </dict>
            </dict>
            <key>EnableTransactions</key>
            <true/>
    </dict>
    </plist>
    EOF
    ```

## Enabling keyboard navigation
For security reasons ssh-askpass defaults to cancel since it's too easy to
press spacebar and accept a connection or other actions which might use
ssh-keys. To make it easier to press `OK`:

* Go to `System Preferences` and then `Keyboard`.

#### Pre 10.11
* Under the `Keyboard` tab, click on `All controls`.

#### 10.11+
* Under the `Shortcuts` tab, click on `All controls`.

Now you can press ⇥+spacebar to press `OK`.

## License
ISC license

## Contributors
* [theseal](https://github.com/theseal)
* [simmel](https://github.com/simmel)
