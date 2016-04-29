# The REDUCE framework

We are able to compute a function to each value of GTS using the MAP framework. We are also able to create buckets on a GTS that will apply a function to all the values of this GTS that belongs to the time intervals of the bucket. This framework also unify all the ticks of a set of GTS. This means, that we are able to reduce a set of BUCKTIZE GTS to a single GTS. This is the main goal of the [REDUCE framework](http://www.warp10.io/reference/frameworks/framework-reduce/). With the fuel stations, we can use the price to compute the average price of the stations near the Brest Airport during the month of november, week by week. And this framework, can also be used to count week by week the number of stations that updates their prices by type of fuel.

## REDUCE parameters

The REDUCE takes one list as parameter. This list contains one or several lists of GTS. It contains also a list of labels to compute an equivalence class on which the mapper function will be applied. The last element of this parameter list is the [reducer function](http://www.warp10.io/reference/reference/#framework-reducers) to compute.

## Compute the average price of the stations in the month of november week by week

On the set of GTS of the november month, first apply a bucketize with a timespan of 604800000000 microseconds (corresponding to one week). Then apply the REDUCE on the result using the SWAP function seen in the previous chapter. In this example all the data of the month of november are loaded. We prefer to have the average price by types of carburant. Then when we apply the reducer, we would like to compute an equivalence class for each types of fuel. Let's do it, by creating as second argument a list containing a single element 'type'. As some stations can possibly have no value during this week (closing station, not updated), apply the [reducer.mean.exclude-nulls](http://www.warp10.io/reference/frameworks/reducer_mean_exclude-nulls/) function on it. This function will ignore null values when computing the mean.

Open and complete the reduce_01.mc2 file, and execute it to compute the mean price of each type of fuel during the month of november, week by week.

## Compute the number of stations updating their prices week by week and by types of fuel

In this the data-set slighlty change from the previous one used. You will direclty manipulate the data with no pre-treatment applied.
To get this information, you first need to apply the same BUCKETIZE on the data, then a different reducer. This time use the function [reducer.count.exclude-nulls](http://www.warp10.io/reference/frameworks/reducer_count_exclude-nulls/) instead, it will computes at each tick the number of measures of Geo Time Series. This function will eclude null value when computing this count. To have a more readable result you can use the function [VALUES]() which, will produce for each GTS a list containing all the values. Here one value corresponds to the number of stations that updates their prices during each weeks of november.

Open and complete the reduce_02.mc2 file, and execute it to know how many stations updates their price during each week of the month of november.
As you can see this value evolve with the time, and is really different week by week.

How can we explain it ? 
This is due to the fact that the data are updatated only when the price changes. The data-set is updated every day. For all the previous GTS, we applied a modification to take in account this particulary.

## Manage an event based data-set

To be able to analyse with the real value the data-set, we load all the points of the month of october and november, then applied a daily bucketize. Once the GTS are bucketize, we are able to fill them with the previous value. At the end we only kept the value of the month of november.

In this exercise, you will work directly on the data of the month of november. First of all, apply a daily bucketize (one day corresponds to 86400000000 microseconds). To create a bucket for each day of the month of november, for each series, you have to specify the parameter lastbucket. Complete this parameter with the timestamp in microsecond of the 1 of december at 0.00am (1448928000000000). Then apply the function [FILLPREVIOUS](http://www.warp10.io/reference/functions/function_FILLPREVIOUS/) on the resulting set of GTS. This function fill each null bucket of a BUCKETIZED set of GTS with the value of the previous bucket. 
Then re-apply the code done on the previous exercise.

Open and complete the reduce_03.mc2 file, and execute it to see week by week the sum of function that updated theirs prices.
