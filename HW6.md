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
 k = 1
 while k <= j :
  print('#', end = "")
  k = k+1
 print()
 j = j-1

```








還沒寫完

Complete this program that reads an integer n and prints the following diamond pattern with 2 * n - 1 asterisks at its widest point. This is the pattern when n is 3:

--*--
-***-
*****
-***-
--*--



``` PYTHON
n = int(input("Enter value of n: "))

# Draw top half and middle of the triangle
for leftStars in range(n) :
   for column in range(2 * n - 1) :
      firstStar = n - 1 - leftStars
      lastStar = n - 1 + leftStars
      if column < firstStar or column > lastStar :
         print("-", end="")
      else :
         print("*", end="")
   print()
# Draw bottom half of the triangle
for leftStars in range(n-2, -1, -1) :
   for column in range((2 * n - 2),-1,-1) :
      firstStar = n - 1 - leftStars
      lastStar = n - 1 + leftStars
      if column < firstStar or column > lastStar :
         print("-", end="")
      else :
         print("*", end="")
   print()
```
