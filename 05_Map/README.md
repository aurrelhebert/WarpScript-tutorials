# The MAP framework

In previous tutorial, you learn how to create time buckets from a set of GTS. In this tutorial, you will learn to update the values of a set of GTS using the [MAP framework](http://www.warp10.io/reference/frameworks/framework-map/). The MAP framework allows you to apply a function on values of a Geo Time SeriesTM that fall into a sliding window. In this tutorial, you will use the mapper to convert all prices in dollars, to compute the derivation of those GTS and finally to kept only the value of GTS superior to 1.08 euros of the 20 stations nearest the Brest airport.

## MAP parameters

Map takes as input a list of parameters. The first element of this list can be one or several lists of GTS. Then there is a [mapper function](www.warp10.io/reference/reference/#framework-mappers). The third and the fourth elements are related to the sliding window, with first an element corresponding to "pre", the width of the sliding window before the value, and in second an element corresponding to "post", the width of the sliding window after the value. The last element corresponds to "occurences" which is the limit of computation of a number. For all elements except the set of GTS and the mapper function a default value 0 can be used, when those elements aren't required.

## Convert the fuel prices from euro to dollars

On the 30 of november the rates between euro and dollar was one euro equals 1.057 dollars. To convert our prices in euro to dollar we have to divide all of our price by 1.057. As there is no mapper to divide value in WarpScpript, the [mapper.mul](http://www.warp10.io/reference/frameworks/mapper_mul/) will be used. This mapper is a single value mapper, which means that it can't have a sliding window. Put 0 for each elements corresponding to the sliding window paramaters. This mapper takes the number to multiply all values as a parameter between the set of GTS and the mapper function.

Open and complete the map_01.mc2 file, and execute it to convert all prices of the november month in dollars.

##  Compute the trend of those GTS and detect the station which raised the most it's prizes.

We will now apply a MAP with the function [mapper.delta](http://www.warp10.io/reference/frameworks/mapper_delta/) which is a sliding window mapper. We will apply the derivation of this GTS of the point after and the one before of the current point. We will have to configure the parameter pre and post of the delta mapper. Then using the BUCKETIZE framework with the function [max](http://www.warp10.io/reference/frameworks/bucketizer_max/) or [sum](http://www.warp10.io/reference/frameworks/bucketizer_sum/), you will be able to see which stations raised the most it's price during the month of november, or add the huge raise between two dates (for both, it should be the same one). To apply the BUCKETIZE on the result set of GTS of the MAP function, you can use the [SWAP](http://www.warp10.io/reference/functions/function_SWAP/) methods. This method inverse two elements on the stack. In this case you can use it to inverse the list open marker and the set of GTS resulting of the MAP operation.

Open and complete the map_02.mc2 file, and execute it to get the prices trend during the month of november and find the station that raised the most its pries.

## Kept GTS which have at least one price superior to 1.08 euros in november

To do that we will apply an other MAP with the function [mapper.gt](http://www.warp10.io/reference/frameworks/mapper_gt/) which is also a sliding window mapper. However, we will use this function as a single value mapper. For each GTS, it will keep only the values that are superior to a value given as a parameter. This value have to be given before the function on the stack. Apply this mapper on the GTS near the Airport for the month of november. To eliminate the GTS with no values, the NONEMPTY function is usable. This function delete from a set of GTS on top of the stack the function that are empty. This will let on top of the stack, a GTS list which have at least one value superior 1.08 euros in november.

Open and complete the map_03.mc2 file, and execute it to get the prices trend during the month of november and find the station that have prices superior to 1.08, you may refind the same station that you see in the previous exercise.
