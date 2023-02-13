605. Can Place Flowers


![圖片](https://user-images.githubusercontent.com/118010660/218507228-00285411-fdfd-4ea6-99f5-e66f48686c1c.png)


You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, return if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule.

 

Example 1:

Input: flowerbed = [1,0,0,0,1], n = 1
Output: true

Example 2:

Input: flowerbed = [1,0,0,0,1], n = 2
Output: false

 

Constraints:

    1 <= flowerbed.length <= 2 * 104
    flowerbed[i] is 0 or 1.
    There are no two adjacent flowers in flowerbed.
    0 <= n <= flowerbed.length

``` java
public class Can_Place_Flowers {

   public boolean canPlaceFlowers(int[] flowerbed, int n) {
      int count = 0;

      if (1 == flowerbed.length) {
         if (flowerbed[0] == 0)
            count++;
         return count >= n ? true : false;
      }

      if (2 == flowerbed.length) {
         if(flowerbed[0] == 0 && flowerbed[1] == 0)
            count++;
         return count >= n ? true : false;
      }

      for (int i = 0; i < flowerbed.length - 1; i++) {
         if (i == 0 && flowerbed[i] == 0 && flowerbed[i + 1] == 0) {
            flowerbed[i] = 1;
            count++;
         } else if ((i == (flowerbed.length - 2)) && flowerbed[i] == 0 && flowerbed[i + 1] == 0) {
            flowerbed[i + 1] = 1;
            count++;
         } else if (flowerbed[i] == 0 && flowerbed[i + 1] == 0 && flowerbed[i + 2] == 0) {
            flowerbed[i + 1] = 1;
            count++;
         }

      }
      return count >= n ? true : false;
   }

   public static void main(String[] args) {
      Can_Place_Flowers sm = new Can_Place_Flowers();
      int[] case1 = { 1, 0, 0, 0, 1 }; // true
      System.out.println("true:" + sm.canPlaceFlowers(case1, 1));

      int[] case2 = { 1, 0, 0, 0, 1 }; // false
      System.out.println("false:" + sm.canPlaceFlowers(case2, 2));

      int[] case3 = {}; // false
      System.out.println("false:" + sm.canPlaceFlowers(case3, 2));

      int[] case4 = { 1, 0, 0, 0, 0, 0, 1 }; // true
      System.out.println("true:" + sm.canPlaceFlowers(case4, 2));

      int[] case5 = { 1, 0, 0, 0, 0, 1 }; // false
      System.out.println("false:" + sm.canPlaceFlowers(case5, 2));

      int[] case6 = { 0, 0, 1, 0, 1 }; // true
      System.out.println("true:" + sm.canPlaceFlowers(case6, 1));

      int[] case7 = { 1, 0, 0, 0, 1, 0, 0 }; // true
      System.out.println("true:" + sm.canPlaceFlowers(case7, 2));

      int[] case8 = { 1 }; // true
      System.out.println("true:" + sm.canPlaceFlowers(case8, 0));

      int[] case9 = { 0 }; // true
      System.out.println("true:" + sm.canPlaceFlowers(case9, 1));
      
      int[] case10 = { 0,0 }; // false
      System.out.println("false:" + sm.canPlaceFlowers(case10, 2));
      
   }
}
```


