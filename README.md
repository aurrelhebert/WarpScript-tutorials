# WarpScript-tutorials
Tutorial to start analysing GTS with WarpScript.

WarpScript is a programming language specific to Geo Time Series analysis<sup>®</sup>. For security reason, WarpScript is an interpreted language, which means that a Warp 10 backend have to be reached to execute a script.

In this tutorial, two different backend can be reached: our sandbox backend or a local docker image. To run your own Warp 10 docker, follow the step available in the chapter 0.

If you want to reach our backend, you can directly start our tutorials with chapter 1.

To execute each mc2 files, there three possibilities. First, you can use the given html files to execute them in a navigator.
Or you can execute the following curl request (or a Post) with the mc2 files on a specified backend.

```
curl -H 'Transfer-Encoding:chunked' --data-binary @file.mc2 $backend
```

And finally, you can use the sublime text with the interpreter available [here](https://github.com/cityzendata/sublime-warpscript).