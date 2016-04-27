# Analyse a set of Geo Time Series<sup>®</sup>

Now we will analyze all the values of the stations located in the Finistère.

## Get the GTS

The GTS chosen as example includes all the prices available during the month of november 2015. In order to have a generic example, those GTS are wrapped. To use it, you will first need to convert the Wrap String to a WarpScript list using the JSON convertion then to unwrap it. Those steps are done in the first lines of the sgts_01.mc2 script.
When execute this script, the element on top of the stack is a list of GTS. It contains all the the "gas oil" fuel GTS located in the Finistère.

## How many stations sells "gas oil" in the finistère?

To get this information the function [SIZE](http://www.warp10.io/reference/functions/function_SIZE/) of a list can be computed. This will give us the number of elements contained in the list on top of the stack. This number corresponds then to the number of stations selling "gas oil" in the finstère. 

Open and complete the gts_01.mc2 file, and execute it to get the find the number of stations in the Finistère.

## Get top less/more expensive stations in the Finistère

In this section, we would like to know which stations are the less/more expensive in the Finistère, at the end of november. To do it we will use the function [LASTSORT](http://www.warp10.io/reference/functions/function_LASTSORT/). This function takes a GTS list and will sort them in ascending order according to their last value.

To get the less expensive station, just use the [GET](http://www.warp10.io/reference/functions/function_GET/) function that can be applied on a list. This function requires a list and the index to get on top of the stack (using GET, you can then find some of the less expensives stations).

To get the more expensive station, the function [REVERSE]() can be applied on the result list produced by LASTSORT. Then using the GET function, you are able to find the more expensives ones. 


Open and complete the gts_02.mc2 file, and execute it to get the less/more expensive station in the Finistère.

