

![圖片](https://user-images.githubusercontent.com/118010660/217548614-460f8adf-607a-4df9-ab8d-e0a9ce6a7498.png)

![圖片](https://user-images.githubusercontent.com/118010660/217549535-0af0307d-2679-49ce-9b10-67874ec3f72c.png)



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

`` java
public class Length_of_Last_Word {
   public int lengthOfLastWord(String s) {
      return s.split(" ")[s.split(" ").length-1].length();
   }
   
   public static void main(String[] args) {
      System.out.println(new Length_of_Last_Word().lengthOfLastWord("sdas asdji"));
   }
}

```
