#android-cordova

### Tl;DR  
[Aliases for ubuntu](/#aliases-i-use)  
[Quickstart](/#quick-start)

###FAQ
> What is in this docker ?

In short, a minimal android sdk and cordova.

> Wait, what ?

http://cordova.apache.org  
https://developer.android.com/guide/index.html

> Just tell me what Cordova is !

Cordova is a cross-platform smartphone application compiler (I guess ?). YOu can code your app like a web app, with html, js, and stuff. (plugins *cough*). You focus on developping an android 'proof of concept' for your app and quickly launch your app on other OS's when you are ready for production.

> Do I need it ?

If you want to start building an app quickly you can be set in no time. Jump to [quickstart](/#quick-start)

> Do I have the skills to start using your docker ? I heard it's complicated.

If you are on a recent linux, installation will be a matter of minutes. Then you can start using the command line aliases I am providing and you will be using docker without even knowing it's there.
https://docs.docker.com/installation/

> I am a windows user and my container just doesn't work ! gradle can't unzip.

Well, neither does my colleague's. Windows can't handle > 260 file paths. Meh. You can use this command instead :

```drun -v /gradle:/gradle -v $PWD:/src -e "GRADLE_USER_HOME=/gradle" kallikrein/android-cordova cordova build ```

Explanation :  
We tried to fix the high size of the gradle folder beeing downloaded at each run by mounting a gradle folder outside of the container (and --rm container afterwards).

With oracle VM getting your windows 'user' folder mounted, you might reach the maximum file path.

So with this command you will create a /gradle folder at the root of your vm and mount it to the cordova container, you also sets the env to know where to write and read gradle files.

If you run several builds in a row you will only download gradle once. If you shut down the boot2docker VM it will be deleted though, since it's in a non-persistent folder.

> I am using boot2docker with [insert proprietary here] and I can't mount my usb ...

I can't help you. I'm not even sure something can be done. We managed to mount a nexus 4 on a windows8 with boot2docker. It required tweaking the usb sharing. But it worked.

> I want something more or the image needs an update.

Email me and I can maintain this image.

### Aliases I use

In ~/.bash_aliases :

```
alias mine='sudo chown -R $USER'
alias drun='docker run -it --rm'
alias cordova='drun --privileged -v /dev/bus/usb:/dev/bus/usb -v $PWD:/src kallikrein/android-cordova cordova'
```

### A note on security :
The commands I proposed to use are ```--privileged```, which means your containers are much more dangerous for your system. If you mess anything up, that is.

> Why should we use ```--privileged``` ?

It's **optionnal**, you can do without this flag, but you won't be able to upload and launch your app on your phone with the built in ```cordova run```, since you need an access to your usb devices.
If you don't want to use usb, you can remove  ```--privileged -v /dev/bus/usb:/dev/bus/usb```.

**NB** : I intend to further enhance this image to display the emulator view. For this feature you will need to mount X11 devices and use the ```--privileged``` flag too.



###Quick Start

Let's create our first app :
(considering you are using my aliases)

```
docker pull kallikrein/android-cordova
```
```
cordova create myAPP
```
(The myAPP folder must NOT exist before using this command.)

```
cd myAPP
```
```
cordova platform add android
```
```
cordova build
```
```
mine ..
```  
If you are launching the app with privilege, you can plug in your phone and :
```cordova run```


### TODO :

Fix gradle. We might be able to install in the image once and for all.