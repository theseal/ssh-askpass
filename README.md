ssh-askpass
===========

ssh-askpass for OS X. Works in (at least) 10.7+ (including Yosemite)

Used to accept(or deny) the use of the private key(s) added to the authentication agent with "ssh-add -c".

![Screenshot](https://github.com/theseal/ssh-askpass/raw/master/sample/ssh-askpass.png)

## Installation

    $ sudo ln -s $PWD/ssh-askpass /usr/libexec/ssh-askpass
    $ chmod +x /usr/libexec/ssh-askpass

### Thanks
[simmel](https://github.com/simmel)
