# iOS Debugging with Xcode Student Notes

This document is primarily a fact sheet to support the "iOS Debugging with Xcode" Udemy Course.
Whenever a website, git repository, or a complex command line is discussed, it will also be listed in this document.  This means you don't need to worry about typing in URLs or commands; you can just copy-paste from here.

## Introduction

- Student's Required Configuration
  - Catalina 10.15.3 (19D76) or later
  - Xcode 11.3.1 (11C504) or later
  - Xcode Command Line Tools for Xcode 11.3.1
- Instructors' Machine Configuration
  - Catalina 10.15.3 (19D76)
  - Xcode 11.3.1 (11C504)
  - Xcode Command Line Tools for Xcode 11.3.1
  - System Preferences
    - Appearance = Dark Mode
  - Keyboard
    - Modifier keys
      - Swapped Control and Caps lock around
  - Display
    - Scaled: Larger Text
  - Accessibility
    - Display: Reduce Motion
  - Terminal Replacement iTerm2 https://www.iterm2.com
  - Command shell modifications oh-my-zsh https://github.com/ohmyzsh/ohmyzsh
    - plugins=(git osx)
  - Hardware
    - iMac Retina 5K Display with 16GB RAM, 512GB Disk (256GB Internal, 256GB External Samsung T5 Drive)
    - WASD Mechanical Keyboard v3 https://www.wasdkeyboards.com
    - Mac Keyboard layout customisation https://github.com/aasmith/mac-wasd-keyboard
      - Switch Type: Cherry MX Brown (Tactile Bump) Sound Dampeners: 0.2mm Travel Reduction
      - Software Key Re-mapping done with [Karabiner Elements](https://karabiner-elements.pqrs.org)
    - Audio Setup https://github.com/faisalmemon/audio-setup
    - Video Setup https://github.com/faisalmemon/video-setup

## Duck Duck Go

- Upstream Official Source Code https://github.com/duckduckgo/iOS
- To get Instructor's Branch 
```
git clone https://github.com/faisalmemon/iOS -b feature/c0 duckduckgo-ios
cd duckduckgo-ios
```
- Install the Brew Package manager from [Brew HomePage](https://brew.sh) using:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
- Install the Carthage Package Manager using Brew `brew install carthage`

## Let's explore the debugger

- Background information on Bloom Filters at https://en.wikipedia.org/wiki/Bloom_filter
- Looking at time-sensitive dynamic code
  - To list breakpoints `br list`
  - To delete breakpoints `br delete`
  - Setting breakpoints on a function and its closures `br set -r DuckDuckGo.FireAnimation.animate` 
  - Setting command action to make each breakpoint print a back trace (bt) and then continue (c)
```
(lldb) br command add
Enter your debugger command(s).  Type 'DONE' to end.
> bt
> c
> DONE
(lldb) 
```
- Breakpoint attachment prerequisites
  - Admin privilege to debug attach `sudo DevToolsSecurity -enable`
  - Scheme setting Run > [Info Tab] > Debug Executable ticked
  - Xcode > Preferences> [Behaviour Top Tab] > [Running Pauses Left Tab] >
    - Ticked Show Navigator "Debug Navigator"
    - Ticked Show Debugger with "Current Views"
- System Debugging preqrequisites (Advanced configuration noting Security/Integrity implications)
  - Restart your computer
  - Press Command+R during boot
  - Supply password
  - Select Utilities > Terminal
  - Type `csrutil enable --without debug`
  - Apple Icon > Restart
- Lifecycle Debugging
  - To breakpoint all viewDidLoad methods in our project `br set -r DuckDuckGo.*.viewDidLoad`
  - See also [Screenshots Walkthrough](./systemDebugConfig.pdf)
- View Hierarchy Debugging
  - View exploration using [Facebook Chisel](https://github.com/facebook/chisel)
  - Installation via brew `brew update; brew install chisel`
  - Make LLDB debugger read in the Chisel extensions:
```
touch ~/.lldbinit
echo "command script import /usr/local/opt/chisel/libexec/fblldb.py" >> ~/.lldbinit
```
- Exploring multi-process debugging
  - Example xpc service https://github.com/faisalmemon/xpc-service-example
```
git clone https://github.com/faisalmemon/xpc-service-example -b feature/c0 xpc-service-example
cd xpc-service-example
```
