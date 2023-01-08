這題雖然被歸類在easy, 但不知道是不是太久沒寫code, 居然花了兩三天才把它寫出來,

一開始學Java6.0到現在已經18, 還以為java又多了一個叫做ListNode的物件,

原來題目只是希望能用LinkList的方式把它寫出來.

![螢幕擷取畫面 2023-01-08 235809](https://user-images.githubusercontent.com/118010660/211206519-603aed53-7044-47fc-9c91-bad9cc6e87cb.png)

You are given two non-empty linked lists representing two non-negative integers. 
The digits are stored in reverse order, and each of their nodes contains a single digit. 
Add the two numbers and return the sum as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.


# Example 1:

Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

# Example 2:

Input: l1 = [0], l2 = [0]
Output: [0]

# Example 3:

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]

Constraints:
* The number of nodes in each linked list is in the range [1, 100].
* 0 <= Node.val <= 9
* It is guaranteed that the list represents a number that does not have leading zeros.

**試題心得**
1. 因為要求有1~100個長度的數字進, 所以不要只想用簡單的int或long最相加
2. 進位的時候因為val只是1~9的數字, 所以進位的部分+1就好, 可以不用再這麼麻煩看進位數是什麼數值
3. 寫完後, 其實想想還是有可以直接用ListNode就可以簡單做完的方法, 未來有時間再來優化

**我的解法**



```java
class Solution {
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
 // 把ListNode取出來變成字串
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
     StringBuilder l1Sum = new StringBuilder();
      StringBuilder l2Sum = new StringBuilder();
      while (l1 != null || l2 != null) {
         if (l1 != null) {
            l1Sum.append(l1.val);
            l1 = l1.next;
         }

         if (l2 != null) {
            l2Sum.append(l2.val);
            l2 = l2.next;
         }
      }

// 因為後面是用陣列相加, 所以轉成Aerray
      String[] test1 = l1Sum.toString().split("");
      String[] test2 = l2Sum.toString().split("");

// add
      String a[];
      String b[];

      if (test2.length > test1.length) {
         a = test2;
         b = test1;
      } else {
         a = test1;
         b = test2;
      }

      String sum[] = new String[128];
      for (int a1 = 0; a1 < a.length; a1++) {
         int aNum = Integer.parseInt(a[a1]);
         if (a1 >= b.length) {
            if (sum[a1] == null)
               sum[a1] = a[a1];
            else {
               int tmp = Integer.parseInt(sum[a1]) + Integer.parseInt(a[a1]);
// 注意事項
// 進位處理, 特別是進位後還有兩位數的
// ListNode.var的數字位數都不相同
               if (tmp >= 10) {
                  sum[a1 + 1] = String.valueOf(tmp / 10);
                  if (sum[a1] == null) {
                     sum[a1] = String.valueOf(tmp % 10);
                  } else {
                     int sumTmp = tmp % 10;
                     sum[a1] = String.valueOf(sumTmp);
                  }
               } else {
                  if (sum[a1] == null)
                     sum[a1] = String.valueOf(tmp);
                  else {
                     int sumTmp = Integer.parseInt(sum[a1]) + Integer.parseInt(a[a1]);
                     sum[a1] = String.valueOf(sumTmp);
                  }
               }
            }
         } else {
            int bNum = Integer.parseInt(b[a1]);

            int tmp = aNum + bNum;
            if (tmp >= 10) {
               sum[a1 + 1] = String.valueOf(tmp / 10);
               if (sum[a1] == null) {
                  sum[a1] = String.valueOf(tmp % 10);
               } else {
                  int sumTmp = Integer.parseInt(sum[a1]) + (tmp % 10);
                  sum[a1] = String.valueOf(sumTmp);
               }
            } else {
               if (sum[a1] == null)
                  sum[a1] = String.valueOf(tmp);
               else {
                  int sumTmp = Integer.parseInt(sum[a1]) + tmp % 10;
                  if(sumTmp >= 10) {
                  // 進位的地方可以直接放1, 會比較簡單
                     sum[a1 + 1] = String.valueOf(sumTmp / 10);
                     sum[a1] = String.valueOf(sumTmp % 10);
                  }else {
                     sum[a1] = String.valueOf(sumTmp);
                  }
               }
            }
         }
      }
      // add end

// 重新塞回ListNode
      ListNode ns1 = new ListNode(Integer.parseInt(sum[0]));
      ListNode stmp;
      stmp = ns1;
      for (String s : sum) {
         if (s == null)
            break;
         ListNode subTmp = new ListNode(Integer.parseInt(s));
         stmp.next = subTmp;
         stmp = stmp.next;
      }
      stmp = ns1.next;
      return stmp;
    }
}
```

// 把字串轉成 ListNode
```java
   public static ListNode createListNode(String input) {
      String s[] = input.replace("[", "").replace("]", "").split(",");
      ListNode start = new ListNode(Integer.parseInt(s[0]));
      ListNode startNode;
      startNode = start;

      for (int i = 1; i < s.length; i++) {
         ListNode node = new ListNode(Integer.parseInt(s[i]));
         startNode.next = node;
         startNode = startNode.next;
      }
      startNode = start;
      return startNode;
   }
```


