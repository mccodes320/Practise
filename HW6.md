**1. Complete the following program to make a table of integers from 0 to n (inclusive) and their square roots. The table should be formatted like this one and display the square roots to the same number of decimal places:**

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
  
**2. Complete the following program that displays:**

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






**3. Complete this program that reads an integer n and prints the following diamond pattern with 2 * n - 1 asterisks at its widest point. This is the pattern when n is 3:**

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




**
4. Consider the follow program that prints a page number on the left or right side of a page. Define and use a new function, isEven, that returns a Boolean to make the condition in the if statement easier to understand.**

提示第四題
1. 先想辦法做一個可以輸入參數的function
2. 再做一個可以return的布林值的function
3. python的布林值是什麼
4. 做一個上面兩個都做得到的function
5. 把判斷改用你的isEven

``` python
def main() :
   page = int(input("Enter page number: "))
   if isEven(page) :
      print(page)
   else :
      print("%60d" % page)


def isEven(page) :
   if page % 2 == 0 :
      return True
   else :
      return False
  
main()
```











