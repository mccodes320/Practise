50. Pow(x, n)


![圖片](https://user-images.githubusercontent.com/118010660/221368235-8ba15e04-f631-4261-9a17-f546c78feecd.png)

Implement pow(x, n), which calculates x raised to the power n (i.e., x^n).

 https://leetcode.com/problems/powx-n/description/

Example 1:

Input: x = 2.00000, n = 10
Output: 1024.00000

Example 2:

Input: x = 2.10000, n = 3
Output: 9.26100

Example 3:

Input: x = 2.00000, n = -2
Output: 0.25000
Explanation: 2-2 = 1/22 = 1/4 = 0.25

 

Constraints:

    -100.0 < x < 100.0
    -231 <= n <= 231-1
    n is an integer.
    -104 <= xn <= 104

``` java
public class Pow {
   public double myPow(double x, int n) {
      DecimalFormat df = new DecimalFormat("###.#####");
      if(n>0)
         return Double.parseDouble(df.format(Math.pow(x, n)));
      else if (n < 0)
         return Double.parseDouble(df.format(Math.pow(x, n)));
      else 
         return 1;
   }

   public static void main(String[] args) {
      Pow pw = new Pow();
      System.out.println(pw.myPow(2.0000, 10));
      System.out.println(pw.myPow(2.1000, 3));
      System.out.println(pw.myPow(2.0000, -2));
   }
}

```
