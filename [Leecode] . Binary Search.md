62. Unique Paths

There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to 2 * 109.

![image](https://github.com/user-attachments/assets/ea66868b-3dbd-4824-b8f7-77a4a3c6d6ed)

Input: m = 3, n = 7
Output: 28

Constraints:

    1 <= m, n <= 100


最短路徑問題, 題目其實不會很難, 但是要回想高中學過的對轉路徑
路徑只有往右跟往下, 所以m跟n要各減一位運算,
配合高中的排列組合 C^m-1 n-1, 答案就出來了
題目有說答案只有2*109次方, 所以極端值C^100 100 可以不用看

'''
public class Unique_Paths_62 {
   public static void main(String[] args) {
//      check(3, 7, 28);
//      check(9, 4, 165); 
//      check(100, 1, 1);
//      check(100, 100, 1);*超多2*10^9
//      check(1, 1, 1);
//      check(3, 3, 6);
      check(51, 9, 1916797311);
   }

   public static void check(int a, int b, int ans) {
      Unique_Paths_62 up = new Unique_Paths_62();
      long sum = up.uniquePaths(a, b);

      if (sum == ans) {
         System.out.println("True: " + a + " " + b + " " + ans + " " + sum);
      } else {
         System.out.println("False: " + a + " " + b + " " + ans + " " + sum);
      }
   }

   public long uniquePaths(int m, int n) {
      if(m<1 || n>100) {
         return 0;
      }
      if(m < n) {
         int tmp = n;
         n = m ; 
         m = tmp;
      }
      
      if (n == 1) {
         return 1;
      }
      if (m == 1) {
         return m;
      }

      int molecular = (m - 1) + (n - 1);
      int Denominator = Math.min(m, n) - 1;

      long molecularSum = molecular;

      for (int i = 1; i < Denominator; i++) {
         int sss = molecular - i;
         System.out.println("\t" + (molecularSum * sss / (Denominator -(i)) )+ " " + molecularSum +" " + sss + " " + Denominator + " " + i);
         molecularSum = molecularSum * sss /  (i+1);
      }

      return (int)molecularSum;
   }
}
'''
![image](https://github.com/user-attachments/assets/39b0673c-5309-4774-819d-d5638d2a696c)
