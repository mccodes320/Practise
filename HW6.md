Complete the following program to make a table of integers from 0 to n (inclusive) and their square roots. The table should be formatted like this one and display the square roots to the same number of decimal places:

  n | Root of n
----|----------
  0 |  0.000000
  1 |  1.000000
  2 |  1.414214
  
``` python
from math import sqrt

n = int(input("Enter a positive integer: "))

print("  n | Root of n")
print("----|----------")
   
for i in range (0,n+1) :
 print ('%3d'%(i), "|" , '%.6f'%(i** 0.5))
 
```
  
Complete the following program that displays:

####
###
##
#

by filling in the correct conditions of the two while loops.

``` python
# Complete the following program that displays:

j = 4
while 0 < j :
 k = 0
 while k <= j :
  print('#', end = "")
  k = k+1
 print()
 j = j-1

```


  
