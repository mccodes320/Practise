這題雖然被歸類在easy, 但不知道是不是太久沒寫code, 居然花了兩三天才把它寫出來
一開始學Java6.0到現在已經18, 還以為java又多了一個叫做ListNode的物件,
原來題目只是希望能用LinkList的方式把它寫出來.



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

