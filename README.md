# WarpScript-tutorials

Tutorial to start analysing Geo Time Series<sup>®</sup> (GTS) with WarpScript.

## What will we do during this tutorial?
In France, the fuel prices is available as open data. We get the price (once a week) of a lot of stations in France. The price of this station can be modelised as a time series as it evolves with time. We know were the station are located, by adding this information the data manipulated become Geo Time Series<sup>®</sup>. In this tutorial, we will learn how we can analysed one month of data. As we are located in Brest, we will analyzed only the stations located in our french department: Finistere (29). After this tutorial, you will be able to load by yourself all the data of a the data of a different french department and analyse it. The fuel station data-set will no longer have any secret for you ! 

During this tutorial, for each steps, the instruction are available in the README.md file. The .mc2 file to complete are available in each step repository. The solution is available in the source repository of each steps.

## Getting started

Clone this repository

```
git clone https://github.com/aurrelhebert/WarpScript-Sample
cd WarpScript-Sample
```

We have no intention of updating the source on WarpScript-Sample. Discard everything "git-like" by deleting the .git folder.

```
rm -rf .git
```

## Set-up WarpScript 

WarpScript is a programming language specific to Geo Time Series<sup>®</sup> analysis. For security reason, WarpScript is an interpreted language, which means that a Warp 10 backend have to be reached to execute your script.

In this tutorial, two different backend can be reached: our sandbox backend or a local docker image. To run your own Warp 10 docker, follow the step available in the chapter 0. If you want to try WarpScript using our sandbox, skip the chapter 0.

To execute each mc2 files, there three possibilities. First, you can use the given html files to execute them in a navigator.
Or you can execute the following curl request (or a Post) with the mc2 files on a specified backend.

```
curl -H 'Transfer-Encoding:chunked' --data-binary @file.mc2 $backend
```

And finally, you can use the sublime text with the interpreter available [here](https://github.com/cityzendata/sublime-warpscript).

Now that WarpScript is set-up, let's start with first tutorial [chapter 1](). As WarpScript is a stack language, you will learn some basic information about the stack manipulation. If you are familiar with those concept go directly to the [chapter 2](). There you will manipulate your first Geo Time Serie<sup>®</sup> in WarpScript.

