![圖片](https://user-images.githubusercontent.com/118010660/218289969-56ffd0df-6e2b-47be-81c6-1e111465085c.png)

Given two strings s and goal, return true if and only if s can become goal after some number of shifts on s.

A shift on s consists of moving the leftmost character of s to the rightmost position.

    For example, if s = "abcde", then it will be "bcdea" after one shift.

 

Example 1:

Input: s = "abcde", goal = "cdeab"
Output: true

Example 2:

Input: s = "abcde", goal = "abced"
Output: false

 

Constraints:

    1 <= s.length, goal.length <= 100
    s and goal consist of lowercase English letters.

解題心得:
1. 用字串切割來做比對比較快
2. 其實可以優化, 計算出的字串是不是可以跟goal依樣, 如果題目字串更常, 重複性更高, 那寫法就要改了


``` java
public class Valid_Anagram {
   public boolean rotateString(String s, String goal) {
      if(s.length() != goal.length())
         return false;
      
      for(int i = s.length() ; i >=0 ; i--) {
         String tmp = s.substring(0,i);
         int first = goal.indexOf(tmp);
         String tmp2 = "";
//         System.out.println("tmp: " + tmp + "\tFirst: " + first);
         if(first > -1) {
            tmp2 = s.substring(i);
            int second = goal.indexOf(tmp2);
//            System.out.println("tmp2: " + tmp2 + " Second: " + second);
            if(second>-1)
               return true;
         }
      }
      return false;
   }

   public static void main(String[] args) {
      Valid_Anagram va = new Valid_Anagram();
      System.out.println("case1 true: " + va.rotateString("abcde", "cdeab"));
      System.out.println("case2 false:" + va.rotateString("abcde", "abced"));
      System.out.println("case3 false:" + va.rotateString("aa", "a"));
      System.out.println("case4 true:" + va.rotateString("bbbacddceeb", "ceebbbbacdd"));
   }
}

```
