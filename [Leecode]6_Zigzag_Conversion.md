![圖片](https://user-images.githubusercontent.com/118010660/220390376-48892ceb-0ed7-4f81-b931-3e4038f53ffd.png)


The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R

And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

 

Example 1:

Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"

Example 2:

Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I

Example 3:

Input: s = "A", numRows = 1
Output: "A"

 

Constraints:

    1 <= s.length <= 1000
    s consists of English letters (lower-case and upper-case), ',' and '.'.
    1 <= numRows <= 1000






```java
public class Zigzag_Conversion {
   public String convert(String s, int numRows) {

      String[] tmp = new String[numRows];
      int upTmp = 0;
      if (numRows >= 3)
         upTmp = numRows + numRows - 2;
      else
         upTmp = numRows;

      char[] c = s.toCharArray();

      if (numRows == 1)
         return s;

      for (int i = 0; i < s.length(); i++) {
//         System.out.println(i + "\t" + upTmp + " " + ((i) % upTmp) + " " + c[i] + " ==> "
//               + (numRows - (numRows - (upTmp - ((i) % upTmp)))));
         if (i == 0) {
            tmp[i] += c[0];
         }
         if (i > 0)
            if (((i + 1) % upTmp) > 0 && ((i + 1) % upTmp) <= numRows) {
               tmp[((i) % upTmp)] += c[i];

//               System.out.println(i + "\t" + upTmp + " " + ((i) % upTmp) + " " + c[i] + " ==> " + (numRows - (upTmp - ((i) % upTmp))));
            } else {
               tmp[(numRows - (numRows - (upTmp - ((i) % upTmp))))] += c[i];
            }
      }

      System.out.println("= = = = =");
      String sol = "";
      for (int i = 0; i < numRows; i++) {
         if (tmp[i] != null) {
            sol += tmp[i].replace("null", "");
//            System.out.println(i + " " + tmp[i].replace("null", ""));
         }
      }

      return sol;
   }

   public static void main(String[] args) {
      Zigzag_Conversion zc = new Zigzag_Conversion();
//      System.out.println("PAHNAPLSIIGYIR".equals(zc.convert("PAYPALISHIRING", 3)));
//      System.out.println("PINALSIGYAHRPI".equals(zc.convert("PAYPALISHIRING", 4)));
      System.out.println("AB".equals(zc.convert("AB",1)));
   }
}
```
