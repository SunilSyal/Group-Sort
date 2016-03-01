Group Sort 

Sorting n elements using selection sort requires 

(n-1) + (n-2) + ------ + 2 + 1			 
i.e.	 
(n * (n-1)/2) 

number of comparisons. But if the elements in the problems are grouped together so that all elements of one group are either greater than or less than all elements of other group, the possible comparisons and interchanges will be certainly less than or equal to the comparisons and the interchanges for all elements taken together. 

This can be proved as follows:

Consider n integers where n >= 2 are divided in r groups with X1, X2, …. Xr number of integers in 1st, 2nd, ….., rth group respectively such that 

X1 + X2 + ------- + Xr = n							
-------------(1)

1 <= Xi < n 	(1 <= i <= r)							
-------------(2)

Consider the groups are in increasing order i.e. all the elements in the first group are less than all the elements of the second group and all the elements of the second group are less than all the elements of the third group and so on. But the elements within a group are not in any particular order then the number of comparisons required is as follows:

Total number of comparisons in selection sort for n elements are:

(n * (n - 1)) / 2

Also 

X1 + X2 + -------- + Xr = n 						
(From 1) 

Multiplying both sides by (n - 1) / 2 where as ((n - 1) / 2 > 0) because n >= 2.

X1 * (n - 1) / 2 + X2 * (n - 1) / 2 + ------- + Xr * (n - 1) / 2 = n * (n - 1) / 2 	
-------------(3)

Also 
	Xi < n 						
		(1 <= i <= r) 		
		(From 2)
	
=>	Xi – 1 < n – 1 					
		(1 <= i <= r)

Also 
	Xi >= 1						
		(1 <= i <= r)

=>	Xi / 2 > 0 				
		(1 <= i <= r)

=>	(Xi / 2) * (Xi – 1) < (Xi / 2) * (n – 1) 

Using this result in (3), we get 

X1 * (X1 – 1)/2 + X2 * (X2 – 1)/2 + -------- + Xr * (Xr – 1) /2 < n * (n – 1) /2

So we have the result that the number of comparisons are less. 

How to make groups?

For +ve numbers: This is a sorting technique that can be done using [] (zint) function or rounding off the numbers. In this technique the numbers are grouped together according to the value (index) associated with them. The index value is calculated like the percentile system i.e. the largest number is given the hundred percentage and others are scored relatively. In the similar fashion while sorting the n numbers, n-1 (the last position in the array of size n) will be associated with the largest number. For example, in the following array arr_1 the largest number is 100.

arr_1 = [47, 81, 2, 22, 3, 25, 87, 6, 42, 47, 50, 23, 100, 17, 48]

Let 	max = 100

In this array there are 15 elements (integers in this example). The max is 100, so 100 should be placed in arr_1[14] (for sorting in ascending order). Now element 100 should be assigned the index value 14 which can be done by normalizing the max (i.e 100) to n-1 (i.e 14) using the following formula:

(max / sum) * C = n – 1 							-------------(4)

The sum is sum of all the numbers in array arr_1 and C is the constant used to normalize max to n-1 and is calculated from the above expression. Obviously the sum is +ve value as there is at least one +ve entry in the list. Also C > 0 as all the variables in the above expression are +ve. The sum for this example comes out to be 600 and C has the value 84. Now using this C, the index value for other elements in the list will be calculated and will be stored in a corresponding position in another array, arr_2 (i.e for the 0th element of the first array, the index value will be stored in the 0th position of the second array arr_2). The following is the formula to calculate the index value for each element. 

arr_2[i] = [ (arr_1[i] / sum) * C]			(0 <= i <= 14)

Using [] function, only integer values will be stored in the arr_2. 

The range of the index values is 0 to n – 1. This can be proved as follows:

For max, the index value is n – 1 i.e. 
(max / sum) * C = n – 1 

We know that max is the largest element of the list i.e 

	arr_1[i] <= max 				
		(0 <= i <= 14)

=>	(arr_1[i] / sum) *C <= (max / sum) * C 	
		(0 <= i <= 14)

Also 
	Sum > 0 	(as there is at least one +ve value) 
And 
	C > 0 

=>	0 <= (arr_1[i] / sum) * C <= n-1 

=>	0 <= [arr_1[i] / sum) * C] <= n-1 

After calculating the index values; search for all the elements with the minimum index value i.e. 0 in the arr_2. Interchange the element of arr_1 with 0 index value with the first element of arr_1. Also interchange the corresponding index values in the arr_2. If there is any other element in arr_1 with index value 0, interchange it the second element of the arr_1 whereas the corresponding index value in the arr_2 will be interchanged with the second element of the arr_2. After n comparisons for 0 index value, all the elements of arr_1 with index value 0 (say X1) are at the first X1 positions in arr_1 i.e 0 to X1 – 1. 

Now sort these elements using selection sort. The total number of comparisons will be 

	X1 * (X1 – 1) / 2

Run the similar procedure for the index value 1 starting from the X1th position in the arr_1 and arr_2. The first interchange will be with the X1th element of the arr_1 as well as in arr_2. Consider there are X2 elements interchanged. It will take 

	X2 * (X2 – 1) /2 

comparisons using selection sort.  

Repeat the same procedure until the index value exceeds n – 1, by incrementing index value by 1 for every next iteration. Repeating the same till (n – 1) index value will lead to a sorted list in ascending order. 

There can be at most n non-empty groups with index values from 0 to n – 1 having only one element in each group. So in that case there is no need of comparisons as each element will be at its proper place. The computations involved in such a case are only to calculate the index values and there will be interchanges according to the index values. In this case there are n comparisons for the element with 0 index value, n – 1 for the index value 1 and so on. So the total number of comparisons will be 

	n * (n – 1) /2 

and the possible number of interchanges are 2 (n – 1) (for both arrays). This is certainly not better than selection sort but certainly not practical also.

Generally, there is data with few elements with same index value and few others with some other index value. In such a case, there are some index values with no elements associated with them. Hence the number of comparisons may drop drastically, especially for large amount of data with a limitation of extra memory required for storage of index values for each element. 

One important thing to point here is that all elements of one group i.e. having the same index values are smaller than or greater than all the elements of some other group with different index value. All the elements of a group will be smaller than all the elements of a group which has larger index value. This can be easily proved as follows:

Consider a and b are two elements with index value i1 and i2. 

Let 	i1 < i2 

Let’s prove that a is smaller than b. Consider C is the constant and sum is the sum of all the elements (equation 4).

Now 	i1 < i2 

=>	[(a / sum) * C] < [(b / sum) * C]

=>	(a / sum) * C < (b / sum) * C

=>	a < b						( as sum and C are +ve numbers) 

So there is no need to compare an element with elements with different index number in the data set. The elements of a group are compared and sorted within their own group only. The groups are already in the ascending order as it is clear from the above result. 

For –ve numbers: There isn’t much difference if –ve numbers are included in the data set. Everything will remain same except the way sum, C and index values, were calculated. In this case the sum will be sum of the absolute values of all the data items. And C will be calculated from the following equation:

	[(max – min) / sum] * C = n – 1;

Also the index values will be calculated in similar way:

	arr_2[i] = [(arr_1[i] / sum) * C]			
		(0 <= i <= 14)

Index values has to be non-negative. 

Rounding off the index values: Same logic can be followed with a small change while calculating the index values. Only change here is to replace the [] function and calculate the index values by rounding off the:

	Math.round ((arr_1[i] / sum ) * C) 

and save the values in arr_2[i]. It will give better results than [] (zint) function. 

Group Sort Recursive: In this variation of sorting algorithm, we will not use the selection sort or any other sorting algorithm within the groups. In this case the above described algorithm will be repeatedly applied to all the groups of the list to form the subgroups until a subgroup has only one or two elements in it. If there is only one element in a subgroup, that means the element is already at its proper place. If there are two elements in a subgroup, they can be simply compared and can be interchanged if required. 
