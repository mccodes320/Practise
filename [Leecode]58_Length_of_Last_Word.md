58. Length of Last Word


Given a string s consisting of words and spaces, return the length of the last word in the string.

A word is a maximal
substring
consisting of non-space characters only.

Example 1:

Input: s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.

Example 2:

Input: s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.

Example 3:

Input: s = "luffy is still joyboy"
Output: 6
Explanation: The last word is "joyboy" with length 6.

 

Constraints:

    1 <= s.length <= 104
    s consists of only English letters and spaces ' '.
    There will be at least one word in s.


![圖片](https://user-images.githubusercontent.com/118010660/217548614-460f8adf-607a-4df9-ab8d-e0a9ce6a7498.png)





``` java
public class Length_of_Last_Word {
   public int lengthOfLastWord(String s) {
      String[] tmp = s.split(" ");
      return tmp[tmp.length-1].length();
   }
   
   public static void main(String[] args) {
      System.out.println(new Length_of_Last_Word().lengthOfLastWord("sdas asdji"));
   }
}
```


![圖片](https://user-images.githubusercontent.com/118010660/217549535-0af0307d-2679-49ce-9b10-67874ec3f72c.png)

``` java
public class Length_of_Last_Word {
   public int lengthOfLastWord(String s) {
      return s.split(" ")[s.split(" ").length-1].length();
   }
   
   public static void main(String[] args) {
      System.out.println(new Length_of_Last_Word().lengthOfLastWord("sdas asdji"));
   }
}

```
