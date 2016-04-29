# Manipulate a Geo Time Serie<sup>®</sup>

Now, let's use WarpScript to manipulate one GTS. We will start to analyse a GTS containing the price of the nearest Station of the Brest Airport.

## Get the GTS

The GTS chosen as example includes all the prices available during the month of november 2015. In order to have a generic example, this GTS is wrapped. To use it, you will first need to unwrap it. That's what is done in the first lines of the gts_01.mc2 script.
When execute this script, the element on top of the stack is a GTS. It contains the GTS containing the price of the "gas oil" fuel.

## Manipulate this GTS - Get its last value

When using a GTS, every value correspong to a specific time since Unix epoch. This time value correspond to a tick.
First of all we would like to get the last price of this stations. So we will apply a reverse sort on this GTS ticks. To do it in WarpScript, the [RSORT](http://www.warp10.io/reference/functions/function_RSORT/) function exists. RSORT will sort, a GTS on top of the stack, in a descending order of its ticks values. Now, that the ticks are ordered the first value of the GTS on top of the stack correspond to this information. How to access to this information ?

To access this information the function [ATINDEX](http://www.warp10.io/reference/functions/function_ATINDEX/) could be used to get the values of the first point of the GTS on top of the stack. ATINDEX takes two parameters: the GTS, and the index of the point.

ATINDEX gives a list as a result. This list contains the following information: the time when the value was emitted, the location (latitude and longitude), the elevation and the value.

Open and complete the gts_01.mc2 file, and execute it to get the last price known during the month of november for this station.

## Manipulate the GTS - Compute the mean price of this station

To compute the mean of all the values that belongs to a GTS, only one function is necessary in WarpScript: [MUSIGMA](http://www.warp10.io/reference/functions/function_MUSIGMA/). This function need a GTS on top of stack and a boolean value (to know if the function apply or not the Bessel correction), and will put the mean and the standard deviation of the GTS on the stack. Let's presume that in this example we apply this correction. The standard deviation is now on top of stack, to delete it, use the function [DROP](http://www.warp10.io/reference/functions/function_DROP/), that delete the element on top of the stack. By doing this, you should now have only the mean value of this GTS on the stack.

Open and complete the gts_02.mc2 file, and execute it to get this station mean fuel price during the month of november.

To get more information about GTS manipulation in WarpScript, check on all the function available on [warp10.io](http://www.warp10.io/reference/reference/#functions-gts).




