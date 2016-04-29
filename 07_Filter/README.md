# The FILTER framework

Congratulation to reach the last part of our tutorial. You are now almost autonomn with GTS analysis, and the fuel stations data-set have now almost zero secret for you.

We will give a last useful tips to compute some analysis on GTS: the use of the [FILTER framework](http://www.warp10.io/reference/frameworks/framework-filter/). This framework is useful to select some specific GTS from a set of GTS. In our case, we will use to it to select only the series corresponding to the fuel type "gas oil", and in a second time we will use it to get the GTS having their last prices known inferior to 1.05 euros.

## FILTER parameters

The FILTER framework takes as input a list of parameters containing one or several lists of GTS. It contains also a list of labels to compute an equivalence class, and a [filter function](http://www.warp10.io/reference/reference/#framework-filters).

## Filter the GTS by labels

We will use the the FILTER framework to get from our set of GTS, only the one corresponding to the "gas oil" fuel type. To do it, use the function [filter.bylabels](http://www.warp10.io/reference/frameworks/filter_bylabels/). This function will select the GTS that match specific labels.
Put in the stack before the filter.bylabels function, a map containing the labels selector. In our case create a map with two elements: 'type' and 'gazole'. Type is the key element, and 'gazole' is the label value.

Open and complete the filter_01.mc2 file, and execute it to select the fuel GTS corresponding to the "gas oil" type.

## Filter the GTS by their last values to compute the number of stations having a price inferior to 1.05 euros.

Some filters functions exist to filter the GTS accoriding to their last value. To get the station with their last value inferior to 1.05 euros, use the function [filter.last.gt](http://www.warp10.io/reference/frameworks/filter_last_gt/). This function takes a number as parameter. 

Open and complete the filter_02.mc2 file, and see how many stations have their last price below 1.05 euros.

You can mix both filters to get the station selling "gas oil" and having their last price below 1.05 euros or another price ! This is the end of this tutorial, thanks for reading it, and don't hesitate to give us your feel back about it.