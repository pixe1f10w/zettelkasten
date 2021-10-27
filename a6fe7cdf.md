---
date: 2021-10-27T16:06
tags:
  - macos
---

# Disabling default keyboard layout on macOS

For some (understandable) reason you cannot remove default latin keyboard layout on macOS, but that can be desirable in case if you [[609a89d9|modified layout]] and don't want to have multiple almost-identical layouts at same time.

So you can do as was supposed at https://apple.stackexchange.com/questions/44921/how-to-remove-or-disable-a-default-keyboard-layout/60521#60521:

1. Change the current input source to your custom keyboard layout.

	cd ~/Library/Prefences
	cp com.apple.HIToolbox.plist com.apple.HIToolbox.plist.bak
	plutil -convert xml1 com.apple.HIToolbox.plist
	nvim com.apple.HIToolbox.plist

2. Remove the input source or input sources you want to disable from the AppleEnabledInputSources dictionary. If there is an AppleDefaultAsciiInputSource key, remove it.
3. Restart.
4. Go to Setting -> Keyboard and remove the default keyboard layout.

Last checked on Catalina and appears to be working solution.

[[z:zettels?tag=macos]]
