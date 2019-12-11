# frida-ios-dump
Pull a decrypted IPA from a jailbroken device. On a Windows WSL host where frida-ps -U isn't working. This version supports:

 * attaching to PID as well as application bundle name.
 * connect to device using TCP rather than USB
 * use SSH key or default root:alpine username/password
  
## Usage

 1. Install [frida](http://www.frida.re/) on device
 2. run frida on device e.g. `./frida-server -v -l 127.0.0.1:27042`
 3. `sudo pip3 install -r requirements.txt --upgrade`
 4. Run usbmuxd/iproxy SSH forwarding over USB (Default 2222 -> 22). e.g. `iproxy 2222 22`
 5. Run usbmuxd/iproxy SSH forwarding over USB (Default 27042 -> 27042). e.g. `iproxy 27042 27042`
 6. Run `./dump.py -t -k /path/to/id_rsa -a <app_name or pid>`

## Support

Python 2.x and 3.x

### issues

If the following error occurs:

* causes device to reboot
* lost connection
* unexpected error while probing dyld of target process
* Paramiko complains about RSA SSH keys if the header is not `BEGIN RSA...`. A hint is given in the error message


please open the application before dumping.


