---
layout: post
title: Fixing Appcelerator Titanium "Simulator session timed out" error
published: true
categories: [tricks, fixes]
---

Having trouble getting your first Appcelerator Titanium app to work? Lots of people who have upgraded to OS X 10.7 and installed a new copy of XCode have been getting this error on attempting to run an Appcelerator demo app:


    [DEBUG] Session could not be started: Error Domain=DTiPhoneSimulatorErrorDomain Code=2 "Simulator session timed out." UserInfo=0x10048c070 {NSLocalizedDescription=Simulator session timed out.}
    [INFO] Launched application in Simulator (99.67 seconds)
    [INFO] Application has exited from Simulator

The fix is to open XCode and install the newest updated iOS simulator.

![XCode configuration](/images/iosinstall.png)

You may as well enable auto-updating while you're at it.

Hope this helps someone save some time, let me know if you're getting this error and still have trouble.