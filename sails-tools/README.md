# Sails Tools 0.11.3

This docker image adds sails generator to the standard sails image  
[Policy](https://www.npmjs.com/package/sails-generate-policy)  
[Response](https://www.npmjs.com/package/sails-generate-response)  
[Generator](https://github.com/balderdashy/sails-generate-generator)

common use :

```bash
docker run --rm -it -v $PWD:/src kallikrein/sails-tools
```

How to create new entities with this docker ?
---

Example: generate a new policy

In the root of your sails app folder
```bash
alias sails-tools="docker run --rm -it -v $PWD:/src kallikrein/sails-tools sails"
sails-tools generate policy <policyName>
```

I want to use another generator, how can i do it ?
---
Pick one of the following options :
- email me with your favorite generator and I will consider adding it to this image
- fork this repository and modify this dockerfile, then either configure your docker hub build to target your fork or build your image locally. You can submit your fork as a PR
- build a new image from this one, add npm install RUN instuctions. This should be the lightest, yet "quick and dirty", solution.
