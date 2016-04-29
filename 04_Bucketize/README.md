# The BUCKETIZE framework

The function used allow some small GTS manipulation but WarpScript offers other rich tools for manipulating the GTS. Five frameworks are available, in this tutorial we will discover the [BUCKETIZE framework](http://www.warp10.io/reference/frameworks/framework-bucketize/). It provides the tooling for putting the data of a geo time serie into regularly spaced buckets. A bucket corresponds to a time interval.  
We will use this bucket to compute the mean value for the month of november for the 20 stations nearest the Brest airport. The stations prices are daily updated, and a pre-treatment was applid on the fuel data-set to ensure it. We can now also use a bucketize to create for example a bucket size of one week and compute weekly average fuel price for each stations. The analysis will be simplify, as all the ticks in our set of GTS will be exactly the same.

## BUCKETIZE parameters

The BUCKETIZE framework takes a list of elements as parameter. This list contains one or several GTS list, a [bucketizer function](http://www.warp10.io/reference/reference/#framework-bucketizers), a lastbucket that specify when start the last bucket (0 mean this will be computed automatically), a bucketcount which is the duration of the bucket (if 0 WarpScript will compute it), and finally a bucketcount which is the number of buckets (if 0 WarpScript will compute it). 

## Get the average price of each GTS for the november month

For the computation of the mean of each GTS during the month of november, a simple BUCKETIZE can be applied. Use the [bucketizer.mean](http://www.warp10.io/reference/frameworks/bucketizer_mean/) as a function, and create only one bucket that will cover all the tick of the GTS. Then you can for example use the function LASTSORT used previously to observe which station were the less/more expensive during the month of november.

Open and complete the bucketize_01.mc2 file, and execute it to get the mean price of each fuel station during the month of november.

## Generate the mean price week by week for each stations

For the computation of the mean price week by week of each GTS during the month of november, a simple BUCKETIZE can be applied. Use the bucketizer.mean as a function, and create buckets which will have a size equals to 604800000000 microseconds (one week). You will get the same GTS but with uniform ticks. 

Open and complete the bucketize_02.mc2 file, and execute it to get the mean price week by week of each fuel station during the month of november.
