# Sails 0.11.3

common use : 

```docker run --rm -it -v $PWD:/src kallikrein/sails```

How to create a new application with this docker ?

```bash
alias sails="docker run --rm -it -v $PWD:/src kallikrein/sails sails"
sails new myApp
```

How to lift it ?

```bash
alias lift="docker run --rm -it -v $PWD:/src -p 1337:1337 kallikrein/sails sails lift"
cd myApp
lift
```
