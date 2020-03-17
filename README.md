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
    - Audio Setup https://github.com/faisalmemon/audio-setup
    - Video Setup https://github.com/faisalmemon/video-setup

## Duck Duck Go

- Upstream Official Source Code https://github.com/duckduckgo/iOS
- To get Instructor's Branch 
```
git clone https://github.com/faisalmemon/iOS -b feature/c0 duckduckgo-ios
cd duckduckgo-ios
```
