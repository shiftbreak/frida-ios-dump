# frida-ios-dump
Pull a decrypted IPA from a jailbroken device. On a Windows WSL host where frida-ps -U isn't working. This version supports:

 * attaching to PID as well as application bundle name.
 * connect to device using TCP rather than USB
 
## Usage

 1. Install [frida](http://www.frida.re/) on device
 2. run frida on device e.g. `./frida-server -v -l 127.0.0.1:27042`
 3. `sudo pip3 install -r requirements.txt --upgrade`
 4. Run usbmuxd/iproxy SSH forwarding over USB (Default 2222 -> 22). e.g. `iproxy 2222 22`
 5. Run usbmuxd/iproxy SSH forwarding over USB (Default 27042 -> 27042). e.g. `iproxy 27042 27042`
 6. Run ./dump.py -t -a -k <location of private key> `Display name` or `Bundle identifier`

For SSH/SCP make sure you have your public key added to the target device's ~/.ssh/authorized_keys file.

```
./dump.py Aftenposten
Start the target app Aftenposten
Dumping Aftenposten to /var/folders/wn/9v1hs8ds6nv_xj7g95zxyl140000gn/T
start dump /var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/AftenpostenApp
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/AFNetworking.framework/AFNetworking
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/ATInternet_iOS_ObjC_SDK.framework/ATInternet_iOS_ObjC_SDK
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/SPTEventCollector.framework/SPTEventCollector
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/SPiDSDK.framework/SPiDSDK
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftCore.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftCoreData.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftCoreGraphics.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftCoreImage.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftCoreLocation.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftDarwin.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftDispatch.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftFoundation.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftObjectiveC.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftQuartzCore.dylib
start dump /private/var/containers/Bundle/Application/66423A80-0AFE-471C-BC9B-B571107D3C27/AftenpostenApp.app/Frameworks/libswiftUIKit.dylib
Generating Aftenposten.ipa

Done.
```

Congratulations!!! You've got a decrypted IPA file.

Drag to [MonkeyDev](https://github.com/AloneMonkey/MonkeyDev), Happy hacking!

## Support

Python 2.x and 3.x


### issues

If the following error occurs:

* causes device to reboot
* lost connection
* unexpected error while probing dyld of target process

please open the application before dumping.


