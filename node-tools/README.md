# Node Tools 4.2.3

This image adds a toolbox-like set of popular node global features:

[nodemon](https://www.npmjs.com/package/nodemon)  
[bower](http://bower.io/)  
[watchify](https://github.com/substack/watchify)  
[webpack](http://webpack.github.io)  

Common use :
```bash
docker run --rm -it -v $PWD:/src kallikrein/node-tools
```

Example of useful alias :
```bash
alias nodemon="docker run --rm -it -v $PWD:/src -p 1337:1337 kallikrein/node-tools nodemon"
alias watchify="docker run --rm -it -v $PWD:/src kallikrein/node-tools watchify"
alias npm="docker run --rm -it -v $PWD:/src kallikrein/node-tools npm"
alias webpack="docker run --rm -it -v $PWD:/src kallikrein/node-tools webpack"
alias webpack-dev-server='drun -v $PWD:/src -p 8080:8080 kallikrein/node-tools:latest sh -c "webpack-dev-server --host 0.0.0.0"'
```

Fixing webpack-dev-server :

```--host 0.0.0.0``` : fixes the server proxying ('this site can't be reached')  
```sh -c "..."``` : fixes the PID 1 signal ignore policy (^C not killing the process). This fix can also solve other node 'watch' issues, ie: grunt, gulp, keepalive policies, etc
