



![圖片](https://user-images.githubusercontent.com/118010660/216773306-51d7b8b1-3294-4735-a65d-426ce9fc2fb9.png)

解題心得:
1. 複習一下 Map 取值
2. 有值就直接把value 變成2, 沒出現的值value就是1
3. 再取值的時候, 只要是1就取出
4. 作者很仁慈, 沒有做類似都只出現一次或是全部都兩次的case

``` java
public class Single_Number {
   public int singleNumber(int[] nums) {
      Map<Integer, Integer> map = new HashMap<Integer, Integer>();
      for (int tmp : nums) {
         if (map.containsKey(tmp)) {
            map.put(tmp, 2);
         } else {
            map.put(tmp, 1);
         }
      }

      Set<Integer> keySet = map.keySet();
      Iterator<Integer> it = keySet.iterator();
      while (it.hasNext()) {
         int key = (int) it.next();
         int value = map.get(key);
         if (value == 1)
            return key;
      }
      return 1;
   }

   public static void main(String[] args) {
      int[] case1 = { 2, 2, 1 };
      System.out.println("case1 2,2,1, output = 1 = > " + new Single_Number().singleNumber(case1));
      int[] case2 = { 4, 1, 2, 1, 2 };
      System.out.println("case1 4,1,2,1,2, output = 4 = > " + new Single_Number().singleNumber(case2));
      int[] case3 = { 1 };
      System.out.println("case1 2,2,1, output = 1 = > " + new Single_Number().singleNumber(case3));
   }
}
```
