
![圖片](https://user-images.githubusercontent.com/118010660/218474960-ca22d481-3dd1-485a-93fd-f59abfcd4361.png)

You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.

You are given an integer array nums representing the data status of this set after the error.

Find the number that occurs twice and the number that is missing and return them in the form of an array.

 

Example 1:

Input: nums = [1,2,2,4]
Output: [2,3]

Example 2:

Input: nums = [1,1]
Output: [1,2]

 

Constraints:

    2 <= nums.length <= 10^4
    1 <= nums[i] <= 10^4

``` java
public class Set_Mismatch {
   public int[] findErrorNums(int[] nums) {
      Arrays.sort(nums);
      int[] soluatiom = new int[2];
      int[] tmp = new int[nums.length];

      for (int i = 0; i < nums.length; i++) {
         int tmpFor = nums[i];
         if (tmp[tmpFor-1] == 0) {
            tmp[tmpFor-1]++;
         } else {
            soluatiom[0] = nums[tmpFor-1];
            tmp[tmpFor-1]++;
         }
      }

      for (int i = 0; i < nums.length; i++) {
         if (tmp[i] == 0) {
            soluatiom[1] = i+1;
            break;
         }
      }
      System.out.println(soluatiom[0] + " " + soluatiom[1]);
      return soluatiom;
   }

   public static void main(String[] args) {
      Set_Mismatch sm = new Set_Mismatch();
      int[] case1 = { 1, 2, 2, 4 }; // [2,3]
      sm.findErrorNums(case1);

      int[] case2 = { 1, 1 }; // [1,2]
      sm.findErrorNums(case2);

      int[] case3 = { 2, 2 }; // [2,1]
      sm.findErrorNums(case3);

      int[] case4 = { 3, 2, 2 }; // [2,1]
      sm.findErrorNums(case4);

      int[] case5 = { 3, 3, 1 }; // [3,2]
      sm.findErrorNums(case5);

      int[] case6 = { 1, 5, 3, 2, 2, 7, 6, 4, 8, 9 }; // [2,10]
      sm.findErrorNums(case6);
   }
}

```
