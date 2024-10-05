Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4

Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1

 

Constraints:

    1 <= nums.length <= 104
    -104 < nums[i], target < 104
    All the integers in nums are unique.
    nums is sorted in ascending order.

![image](https://github.com/user-attachments/assets/9e2c8b35-6ce5-41e3-b889-9efc780f31f9)


```
package com.macro.sort;

public class binarySearch {
    public static void main(String[] args) {

        binarySearch bs = new binarySearch();
        int[] number = {2,5,8,12,16,23,39,56,72,91};
        bs.resolt(number, 23, 5);

        int[] number2 = {-1,0,3,5,9,12};
        bs.resolt(number2, 9, 4);

        int[] number3 = {-1,0,3,5,9,12};
        bs.resolt(number3, 2, -1);

        int[] number4 = {};
        bs.resolt(number4, 2, -1);

        System.out.println();
    }

    public void resolt (int[] nums, int target, int answer){
        if(search(nums,  target,  0,  nums.length-1) != answer){
            System.out.println(nums.toString() + " " + target + " is worse");
        } else{
            System.out.print("Success, " + target + ", " );
            for(int tmp : nums)
                System.out.print(tmp + " ");
            System.out.println();
        }
    }


    public int search(int[] nums, int target, int start, int latest) {
        int mid = (start + latest)/ 2;

        if(start>latest){
            return -1;
        }

        if(target < nums[mid]) {
            return search(nums, target, start, latest-1);
        } else if(target > nums[mid]) {
            return search(nums, target, mid+1 , latest) ;
        } else if (target == nums[mid]) {
            return mid;
        } else{
            return  -1;
        }
    }
}

```

