

![圖片](https://user-images.githubusercontent.com/118010660/232190282-5d842d1e-6c29-458b-b17d-73b3e12f945d.png)

``` java
package leecode;
//Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

//
//An input string is valid if:
//
//    Open brackets must be closed by the same type of brackets.
//    Open brackets must be closed in the correct order.
//    Every close bracket has a corresponding open bracket of the same type.

public class Valid_Parentheses_20 {
   public boolean isValid2(String s) {
      int check = 0;
      int checkNum = 0;
      if (s.length() % 2 != 0)
         return false;
      char[] carray = s.toCharArray();
      for (int i = 0; i < carray.length; i++) {
         switch (carray[i]) {
         case '(':
            checkNum++;
            check = 0;
            break;
         case ')':
            checkNum--;
            if (check < 0)
               check--;
            check--;
            if (i == 0 || i + check < 0 || carray[i + check] != '(')
               return false;
            break;
         case '{':
            checkNum++;
            check = 0;
            break;
         case '}':
            checkNum--;
            if (check < 0)
               check--;
            check--;
            if (i == 0 || i + check < 0 || carray[i + check] != '{')
               return false;
            break;
         case '[':
            checkNum++;
            check = 0;
            break;
         case ']':
            checkNum--;
            if (check < 0)
               check--;
            check--;
            if (i == 0 || i + check < 0 || carray[i + check] != '[')
               return false;
            break;
         default:
            return false;
         }
      }

      if (checkNum != 0)
         return false;
      return true;
   }

   public boolean isValid(String s) {
      if (s.length() % 2 != 0)
         return false;
      char[] carray = s.toCharArray();
      for (int i = 1; i < carray.length; i++) {
         if (carray[i] == ')' && carray[i - 1] == '(') {
            if(carray.length == 2) {
               return true;
            }
            String a = s.substring(0, i-1);
            String b = s.substring(i+1, s.length());
//            System.out.println("(a:" + a);
//            System.out.println("(b:" + b);
            String add = a + b;
            if(add.length() != 0) {
               return isValid(add);
            }else {
               return true;
            }
         }
         
         else if (carray[i] == '}' && carray[i - 1] == '{') {
            if(carray.length == 2) {
               return true;
            }
            String a = s.substring(0, i-1);
            String b = s.substring(i+1, s.length());
//            System.out.println("{a:" + a);
//            System.out.println("{b:" + b);
            String add = a + b;
            if(add.length() != 0) {
               return isValid(add);
            }else {
               return true;
            }
         }
         
         else if (carray[i] == ']' && carray[i - 1] == '[') {
            if(carray.length == 2) {
               return true;
            }
            String a = s.substring(0, i-1);
            String b = s.substring(i+1, s.length());
//            System.out.println("[a:" + a);
//            System.out.println("[b:" + b);
            String add = a + b;
            if(add.length() != 0) {
               return isValid(add);
            }else {
               return true;
            }
         }
      }
      return false;
   }

   public static void main(String[] args) {
      Valid_Parentheses_20 v = new Valid_Parentheses_20();
//      System.out.println(v.isValid("()"));
//      System.out.println(v.isValid("()[]{}"));
//      System.out.println(v.isValid("(]"));
//      System.out.println(v.isValid("([)]"));
//      System.out.println(v.isValid("{[]}"));
//      System.out.println(v.isValid("{"));
//      System.out.println(v.isValid("(("));
//      System.out.println(v.isValid("){"));
//      System.out.println(v.isValid("()))"));
      System.out.println(v.isValid("(([]){})"));

   }
}


```

