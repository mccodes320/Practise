4. Median of Two Sorted Arrays


![圖片](https://user-images.githubusercontent.com/118010660/219064334-917c2777-6092-4fb7-8f2c-cb934225f5e8.png)


Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

 

Example 1:

Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.

Example 2:

Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.

 

Constraints:

    nums1.length == m
    nums2.length == n
    0 <= m <= 1000
    0 <= n <= 1000
    1 <= m + n <= 2000
    -106 <= nums1[i], nums2[i] <= 106

解題心得:
1. 善用Java原生工具, 像是陣列相加, 排列
2. 答案要有小數點, 
3. 中位數就是就分基數偶數, 基數就是最中間的數是答案, 偶數就是把最中間兩數相加除二


``` java
package leecode;

import java.util.Arrays;

public class Median_of_Two_Sorted_Arrays {
   public double findMedianSortedArrays(int[] nums1, int[] nums2) {
      int length = nums1.length + nums2.length;
      int[] tmp = new int[length];

      System.arraycopy(nums1, 0, tmp, 0, nums1.length);
      System.arraycopy(nums2, 0, tmp, nums1.length, nums2.length);

      Arrays.sort(tmp);
//      for (int t : tmp)
//         System.out.print(t + " ");

//      System.out.println();
      if (length % 2 == 1)
         return tmp[length / 2];
      else {
//         System.out.println("M1: " + ((length / 2) - 1) + " = " + tmp[((length / 2) - 1)]);
//         System.out.println("M2: " + length / 2 + " = " + tmp[length / 2]);
//         int a = tmp[((length / 2) - 1)];
//         int b = tmp[length / 2];
//         System.out.println("==> " + (double)7/2);
         return (double) (tmp[((length / 2) - 1)] + tmp[length / 2]) / 2;
      }
   }

   public static void main(String[] args) {
      Median_of_Two_Sorted_Arrays nt = new Median_of_Two_Sorted_Arrays();
      int[] Case1nums1 = { 161, 170, 163, 168, 177 };
      int[] Case1nums2 = { 175, 155, 171, 179, 150 };
      System.out.println("Case1(169): " + nt.findMedianSortedArrays(Case1nums1, Case1nums2));

      int[] Case2nums1 = { 1, 2, 3, 3 };
      int[] Case2nums2 = { 4, 7, 8, 8, 9 };
      System.out.println("Case2(4): " + nt.findMedianSortedArrays(Case2nums1, Case2nums2));

      int[] Case3nums1 = { 1, 2, 2, 3, 3 };
      int[] Case3nums2 = { 4, 7, 8, 8, 9 };
      System.out.println("Case3(3.5): " + nt.findMedianSortedArrays(Case3nums1, Case3nums2));

      int[] Case4nums1 = { 1, 3 };
      int[] Case4nums2 = { 2 };
      System.out.println("Case4(2.0): " + nt.findMedianSortedArrays(Case4nums1, Case4nums2));

      int[] Case5nums1 = { 1, 2 };
      int[] Case5nums2 = { 3, 4 };
      System.out.println("Case5(2.5): " + nt.findMedianSortedArrays(Case5nums1, Case5nums2));
   }
}

```

