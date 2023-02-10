
![圖片](https://user-images.githubusercontent.com/118010660/218110360-bc1c5866-d289-42f3-8c05-f4d282c7530c.png)


Given a pattern and a string s, find if s follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in s.

 

Example 1:

Input: pattern = "abba", s = "dog cat cat dog"
Output: true

Example 2:

Input: pattern = "abba", s = "dog cat cat fish"
Output: false

Example 3:

Input: pattern = "aaaa", s = "dog cat cat dog"
Output: false

 

Constraints:

    1 <= pattern.length <= 300
    pattern contains only lower-case English letters.
    1 <= s.length <= 3000
    s contains only lowercase English letters and spaces ' '.
    s does not contain any leading or trailing spaces.
    All the words in s are separated by a single space.



解題心得
1. 雖然範例給了很多類似左右對稱的範例, 但是題目沒說是



``` java
public class Word_Pattern {

   public boolean wordPattern(String pattern, String s) {
      if (1 > pattern.length() || pattern.length() > 300)
         return false;
      if (1 > s.length() || s.length() > 3000)
         return false;
      String[] sArray = s.split(" ");
      if (pattern.length() != sArray.length)
         return false;

      Map<String, String> map = new HashMap<String, String>();

      for (int i = 0; i < pattern.length(); i++) {
         String p1 = pattern.substring(i, i + 1);

         String a1 = sArray[i];

         if (map.get(p1) == null) {
            if (map.containsValue(a1))
               return false;
            map.put(p1, a1);

         } else if (!map.get(p1).equals(a1))
            return false;
      }

      return true;
   }

   public static void main(String[] args) {
      System.out.println("Case1, true = > " + new Word_Pattern().wordPattern("abba", "dog cat cat dog"));
      System.out.println("Case2, false = > " + new Word_Pattern().wordPattern("abba", "dog cat cat fish"));
      System.out.println("Case3, false = > " + new Word_Pattern().wordPattern("aaaa", "dog cat cat dog"));
      System.out.println("Case4, false = > " + new Word_Pattern().wordPattern("abcd", "dog cat cat dog"));
      System.out.println("Case5, false = > " + new Word_Pattern().wordPattern("abccda", "dog cat cat cat cat dog"));
      System.out.println("Case6, false = > " + new Word_Pattern().wordPattern("abba", "dog dog dog dog"));
      System.out.println("Case7, true = > " + new Word_Pattern().wordPattern("abc", "b c a"));
      System.out.println("Case8, false = > " + new Word_Pattern().wordPattern("aaa", "aa aa aa aa"));
   }
}

```
