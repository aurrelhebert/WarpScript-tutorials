# WarpScript Stack

WarpScript is a stack related programming language. This means that to compute an operation you first have to put all the parameters on the stack, then put the operator. Then if a result is produced, it will be pushed on top of the stack.

## Single operator

Let's start with a simple WarpScript function: [NOW](http://www.warp10.io/reference/functions/function_NOW/). This function will put on the stack the current time (in microseconds) since the Unix epoch.

First fill the file stack_01 with the keyword NOW, then execute it. A corret mc2 file is available in the source repository.

## Basic operation in WarpScript

Let's compute an operation in WarpScript, but first, in WarpScript, you will find commentary and variable types. 
The following WarpScript example list all the available basic types.

``
// This is a commentary
'a'      // string value
true     // boolean value
42        // long value
3.14159    // double value
```

To compute an operation (for example an addition), put the two elements before the operator [+](http://www.warp10.io/reference/functions/function_ADD/) on the stack.
You will get the result on top of the stack. Open and complete the file stack_02.mc2, then execute it. A corret mc2 file is available in the source repository.

## Structure and function

In WarpScript hundreds of functions are available, you can access the documentation [here](http://www.warp10.io/reference/reference/).
In WarpScript, it's possible to build structure as [List or Map](http://www.warp10.io/reference/reference/#functions-lists-maps).
The structure to build a List in WarpScript is as followed. First put a marker to open a list, then the elements to add. 

```
[ 'elem' 'elem2' ]
```

Let's play with it, in the file stack_03.mc2, build a new list containing two elements: 1 and 3. Then add the elements 2 using the operator [+](http://www.warp10.io/reference/functions/function_ADD/) on this list. Now to sort this list, apply the function [LSORT](http://www.warp10.io/reference/functions/function_LSORT/) on it. This will sort the GTS in a ascending order. To sort the list in a descending order, apply the [REVERSE](http://www.warp10.io/reference/functions/function_REVERSE/) function. Once the file stack_03 is completed, execute it. A corret mc2 file is available in the source repository.