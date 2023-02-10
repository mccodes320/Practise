
![圖片](https://user-images.githubusercontent.com/118010660/218127629-b5899161-afe4-4ef0-8a95-70215c0c7d90.png)



Given a string s, find the length of the longest
substring
without repeating characters.

 

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

 

Constraints:

    0 <= s.length <= 5 * 104
    s consists of English letters, digits, symbols and spaces.

``` java

public class Longest_Substring_Without_Repeating_Characters {
   public int lengthOfLongestSubstring(String s) {
      Map<Integer, StringBuilder> sumList = new HashMap<Integer, StringBuilder>();
      for (int i = 0; i <= s.length(); i++) {
         List<String> lst = new ArrayList<String>();
         StringBuilder sb = new StringBuilder();
         for (int j = i; j < s.length() ; j++) {
            String tmp = s.substring(j, j + 1);
            if (lst.contains(tmp)) {
               sumList.put(sb.length(), sb);
               break;
            }
            lst.add(tmp);
            sb.append(tmp);
         }
         sumList.put(sb.length(), sb);
      }

//      for(int k = 0 ; k < sumList.size() ; k++) {
//         System.out.println(k + " = > " + sumList.get(k));
//      }
      if (sumList.size() == 0)
         return 0;
      return sumList.get(sumList.size() - 1).length();
   }

   public static void main(String[] args) {
      Longest_Substring_Without_Repeating_Characters ls = new Longest_Substring_Without_Repeating_Characters();
      System.out.println("Case 1, abcabcbb: 3 = > " + ls.lengthOfLongestSubstring("abcabcbb"));
      System.out.println("Case 2, bbbbb: 1 = > " + ls.lengthOfLongestSubstring("bbbbb"));
      System.out.println("Case 3, pwwkew: 3 = > " + ls.lengthOfLongestSubstring("pwwkew"));
      System.out.println("Case 4, : 0 = > " + ls.lengthOfLongestSubstring(""));
      System.out.println("Case 5, : 1 = > " + ls.lengthOfLongestSubstring(" "));

   }
}

```
