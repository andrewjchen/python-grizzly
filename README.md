# python-grizzly
python-grizzly is a usb library to control the PiE GrizzlyBear Motor Controller. Currently only supports linux and is only tested on ubuntu.

## Dependencies
| Libary or package         | How to install                |
| --------------------------|:-----------------------------:|
| pyusb                     | sudo pip install pyusb        |
| xboxdrv (example only)    | sudo apt-get install xboxdrv  |

## Installation

From pip: `sudo pip install grizzly`
From source: `python setup.py install`

(Installation will automatically install udev rules for the grizzly

# Usgae examples

To use this library, look at the source or look at example/RunGrizzly.py
Try using RunGrizzly.py:

1. Plug in xbox controller and grizzly.
2. Power on the grizzly.
3. Run sudo python RunGrizzly.py
4. Now the right analog stick in the y-direction controls the Grizzly throttle.

Note that you must run python with sudo to gain access to usb privileges.
Alternatively, you can copy the 50-grizzlybear.rules file into your /etc/udev/rules.d folder.
You will be given non-root access to the grizzly as soon as you plug it in. 
There is another udev rule 50-xboxcontroller.rules that grants non-root access
to the 360 controller. You might need to be added to the uinput group to use it.

xbox_read.py shamelessly copypasta'd from http://github.com/zephod/lego-pi
It could use some refactoring. If somebody wants to write a good parser for it.

xboxdrv is kinda buggy. It can be annoying to try and connect to the xbox
controller. Usually it gets autoloaded when you plug it in and the driver cannot
get a usb lock on it. Try running:
$ sudo rmmod xpad
then trying RunGrizzly.py
