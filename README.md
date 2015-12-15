# dockerfiles

All dockerfile in this repository are built and publicly available on [docker hub](https://hub.docker.com/) at [my repos](https://hub.docker.com/u/kallikrein/)

###Install Docker

These images require [docker](https://www.docker.com/).  
If you're new to docker and want to try it on your ubuntu server, my quick install command is :
```sh
wget -qO- https://get.docker.com/ | sh
```

###Base images :

[ubuntu](/ubuntu)  
Adds some utilities to the standard ubuntu image.  
Most of these are required if your project depends on external sources : GET, git, python, g++  

[node](/node)  
Just node. It is built from kallikrein/ubuntu, meaning that [node-gyp make g++]-dependent "post npm install" compilation will succeed.

[sails](/sails)  
The very popular [back-end javascript framework](http://sailsjs.org/).

###Tool boxes :

[sails-tools](/sails-tools)  
Built from kallikrein/sails, this image has some added custom generator to power up sails even further.

[node-tools](/node-tools)
This image is the top layer of my image stack, it adds to sails-tools some more node package installed globally.

##Why use these docker images ?

A very simple reason : avoid installing a whole stack of softwares after each reinstall, or at every project start. 
I am a freelance developper and appreciate reducing the launch time of my projects to the bare minimum. I occasionnaly start a personnal project and appreciate reproducing dev and prod environment with ease.  
Docker offers a lot of comfort, speed and agility to my back end development experience.

###Are these images safe ?

All my images are built following the same set of rules, some of them direct application of [dockerfile best practices](https://docs.docker.com/engine/articles/dockerfile_best-practices/), some are my own opinionated standardization.

1. Containers should be ephemeral.  
All these images are best used with ```--rm```, they should not store any data anywhere else than in the folder you mount them with.  
Ephemeral doesn't mean that you can't have a 'node' container running for years, without restarting. It means that if you want to restart, it should be *possible* to instantiate a new container from the base image.

2. Containers starting at 'node' allways have the same volume and workdir folder called '/src'.  
```VOLUME /src```  
```WORDIR /src```  
The most frequent use I have is to mount the current folder and I almost allways use ```docker run --rm -it```  

3. Images are built without ```ADD``` or ```COPY```.  
I try to maintain images that are like package of softwares. I use standard installation methods, like ```wget``` or  
```npm i -g```.
The image build steps are only dependent on the dockerfile and not to files living in the folder (that you obviously *shouldn't* trust).  
Check the dockerfiles int the subfolders of this repository for more details on image builds.

###Will these images change without notice ? Will you update them when new versions are released ?  
I try not to bump version in the middle of an ongoing project.  
I use tags, so if you are fine with one the image, you can use its version tags and be sure that the docker won't be modified without notice.  
The 'latest' tag is allways built with the dockerfile on the named branch HEAD, so it is updated with every commit I push to these branches. Version tags are built on github 'release' tags and should never change.  
If you want to continue using my image collection (ie : don't want to dive into the docker hub build hooks), you can fork this repo, build your updated image locally and send me a PR for update.

###I don't understand how to use your images

There are some small commands on the respective README.md files in each folder.  
I will, someday, write tutorials on how to kickstart a node or sails backend server with docker.

