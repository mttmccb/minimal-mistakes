---
title: "Setting up a Microsoft Natural Ergonomic 4000 Keyboard on OSX"
tags:
- keyboard
- setup
---

{% include base_path %}

While trying to get my new [Microsoft Ergonomic 4000 Keyboard](https://www.microsoft.com/hardware/en-gb/p/natural-ergonomic-keyboard-4000) setup on my Mac I hit a few problems, here are the solutions. 
![Surprisingly comfortable to type and relatively cheap at £35](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_5696c12925981d356847932b_1452720430400__img.jpg) Surprisingly comfortable to type and relatively cheap at £35 

## Installing IntelliType
 
The first being OSX El Capitan wouldn't let me install the driver (
[IntelliType 8.2](https://www.microsoft.com/hardware/en-gb/p/natural-ergonomic-keyboard-4000#support)). After a bit of hunting I had to do the following 

* Boot to the Recovery partition by restarting the Mac and holdling down ⌘ and R 
* Open **Terminal** from Utilities and enter: csrutil disable
* Restart
* Install IntelliType by right clicking the Microsoft Desktop Installer and browsing to Contents/Resources and then right-clicking to open **Microsoft Desktop.mpkg**
* Then I just went through the normal installation and it will restart
* Boot to the recovery partition again
* Open the Terminal again and enter: csrutil enable
* Restart back into El Capitan 

Thanks [Kurt Lang](https://discussions.apple.com/message/29099432#29099432). 

## Add the Microsoft Keyboard Helper to Login Items

* Open **System Preferences**;
* Go to **Users & Groups &gt; {your user} &gt; Login Items**; 
* Click **+** icon under the Login Items list;
* When Finder window opens, press ⇧ + ⌘ + G
* When a form appears, paste this into it: `/Library/PreferencePanes/Microsoft Keyboard.prefPane/Contents/Resources/;`
* Select the file **MicrosoftKeyboardHelper**, and press **Add** 

Thanks [Artem Gordinsky](http://apple.stackexchange.com/a/79621). 

## Keymappings
 
I still haven't resolved the key mappings issue, it's the usual problem of the # being in the wrong place, I'll get to that later as the obvious ways to fix it haven't worked. 
Getting the more recent additions like Mission Control to work with one of the function keys isn't working as expected too. 

## Update: 14/01/2015
 
I decided to return the keyboard and I'm getting a Microsoft Sculpt instead. It's just a little too big and the extra buttons, while nice, I can't see myself using them, I have a programmable mouse and trackpad so I think a minimal keyboard is fine. I'm sure I'll blog about the new one when it arrives. 

That said the final part of the puzzle was simply setting the correct input source using the following steps 

* Open **System Preferences**
* Open **Keyboard &gt; Input Sources**
* Add **British - Microsoft** (US Intl is also there) 

This sorted the keys being in the wrong place. I suspect the Sculpt will need this too.
