# Node Tools 4.2.3

This image adds a toolbox-like set of popular node global features:

[nodemon](https://www.npmjs.com/package/nodemon)  
[bower](http://bower.io/)  
[watchify](https://github.com/substack/watchify)  

Common use :
```bash
docker run --rm -it -v $PWD:/src kallikrein/node-tools
```

Example of useful alias :
```bash
alias nodemon="docker run --rm -it -v $PWD:/src -p 1337:1337 kallikrein/node-tools nodemon"
alias watchify="docker run --rm -it -v $PWD:/src kallikrein/node-tools watchify"
alias npm="docker run --rm -it -v $PWD:/src kallikrein/node-tools npm"
```
