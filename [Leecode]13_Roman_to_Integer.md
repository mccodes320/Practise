![圖片](https://user-images.githubusercontent.com/118010660/215507288-1d3c4939-e6fa-439d-9f4e-634bfc9a02cb.png)

程式難度偏易, 大概只花了1小時可以解決

```java
package leecode;

import java.util.HashMap;
import java.util.Map;

/**
 * 13. Roman to Integer https://leetcode.com/problems/roman-to-integer/
 * 
 * @author Macro
 *
 */
public class reste {

   public int romanToInt(String s) {
      Map<String, Integer> roman = Map.of("I", 1, "V", 5, "X", 10, "L", 50, "C", 100, "D", 500, "M", 1000);
      int count = 0;
      for (int i = 0; i < s.length(); i++) {
         String tmp = s.substring(i, i + 1);
//         System.out.println(tmp + " " + roman.get(tmp));
         int first = roman.get(tmp);

         // 大於0才可以做前向比對
         if (i > 0) {
            // 取出前一項的值
            String rtmp = s.substring(i - 1, i);
            int before = roman.get(rtmp);
            如果說上
            // 如果前巷比後巷還小, 就代表要做減法
            if (before < first) {
               // 先把前面加錯的減掉
               count -= before;
               // 再把該加的加上去
               count += (first-before);
            } else {
               count += roman.get(tmp);
            }
         } else {
            count += roman.get(tmp);
         }
//         System.out.println(count);
      }
      return count;
   }

   public static void main(String[] args) {
      String case1 = "III";
      System.out.println(case1 + " => " + new reste().romanToInt(case1) + " Soluation: 3");

      String case2 = "LVIII";
      System.out.println(case2 + " => " + new reste().romanToInt(case2) + " Soluation: 58");

      String case3 = "MCMXCIV";
      System.out.println(case3 + " => " + new reste().romanToInt(case3) + " Soluation: 1994");

      String case4 = "CM";
      System.out.println(case4 + " => " + new reste().romanToInt(case4) + " Soluation: 900");
   }
}


```
