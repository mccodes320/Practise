628. Maximum Product of Three Numbers

![圖片](https://user-images.githubusercontent.com/118010660/218321128-633b9bd4-1146-44f1-982f-9617dfe51410.png)


Given an integer array nums, find three numbers whose product is maximum and return the maximum product.

 

Example 1:

Input: nums = [1,2,3]
Output: 6

Example 2:

Input: nums = [1,2,3,4]
Output: 24

Example 3:

Input: nums = [-1,-2,-3]
Output: -6

 

Constraints:

    3 <= nums.length <= 104
    -1000 <= nums[i] <= 1000

解題心得:
1. 題目訂在easy, 就代表說不要把它複雜化
2. 善用 Arrays.sort
3. 題目所述, 陣列內任3個值組成最大值
4. 難的地方是複數多寡會影響算法, 如兩個負數為正



``` java
public class Maximum_Product_of_Three_Numbers {
   public int maximumProduct(int[] nums) {

      Arrays.sort(nums);

      int negative[] = new int[nums.length];
      int negativeNum = 0;
      int positive[] = new int[3];
      int positiveNum = 0;
      // 計算負數
      for (int i = 0; i < nums.length && negativeNum < nums.length; i++) {
         int tmp = nums[i];
         if (tmp < 0) {
            negative[negativeNum] = tmp;
            negativeNum++;
         }
      }
      Arrays.sort(negative);
      // 計算正數
      for (int i = nums.length - 1; i >= 0 && positiveNum < 3; i--) {
         int tmp = nums[i];
         if (tmp >= 0) {
            positive[positiveNum] = tmp;
            positiveNum++;
         }
      }
      Arrays.sort(positive);

      // 白癡方法只要不符合就直接給最大負數
      int sum[] = new int[4];
      if (negativeNum >= 3)
         sum[0] = negative[negativeNum - 3] * negative[negativeNum - 2] * negative[negativeNum - 1];
      else
         sum[0] = Integer.MIN_VALUE;

      if (negativeNum >= 2 && positiveNum >= 1)
         sum[1] = negative[0] * negative[1] * positive[2];
      else
         sum[1] = Integer.MIN_VALUE;

      if (negativeNum >= 1 && positiveNum >= 2)
         sum[2] = negative[0] * positive[1] * positive[2];
      else
         sum[2] = Integer.MIN_VALUE;
      if (positiveNum >= 3)
         sum[3] = positive[0] * positive[1] * positive[2];
      else
         sum[3] = Integer.MIN_VALUE;
      Arrays.sort(sum);

      return sum[3];
   }

   public static void main(String[] args) {
      Maximum_Product_of_Three_Numbers mp = new Maximum_Product_of_Three_Numbers();
      int case1[] = { 1, 2, 3, 6, 5 };
      System.out.println("case1(90) : " + mp.maximumProduct(case1));

      int case2[] = { 1, 2, 3 };
      System.out.println("case2(6) : " + mp.maximumProduct(case2));

      int case3[] = { 1, 2, 3, 4 };
      System.out.println("case3(24) : " + mp.maximumProduct(case3));

      int case4[] = { -1, -2, -3 };
      System.out.println("case4(-6) : " + mp.maximumProduct(case4));

      int case5[] = { -100, -98, -1, 2, 3, 4 };
      System.out.println("case5(39200) : " + mp.maximumProduct(case5));

      int case6[] = { 1, 0, 100 };
      System.out.println("case6(0) : " + mp.maximumProduct(case6));

      int case7[] = { -1, -2, -3, -4 };
      System.out.println("case7(-6) : " + mp.maximumProduct(case7));
   }
}
```

