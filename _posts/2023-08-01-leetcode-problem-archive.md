---
layout: post
category: 2023
---


> --- Array / String     
> [LeetCode 14: Longest Common Prefix](#)    
> [LeetCode 121: Best Time to Buy and Sell Stock](#)     
> [LeetCode 392: Is Subsequence](#)     
> --- Linked List       
> [LeetCode 2: Add Two Numbers](#)




### [LeetCode 14: Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/?envType=study-plan-v2&envId=top-interview-150)        
문제 요구사항:        
주어진 문자열 배열에서 가장 긴 공통의 접두사(prefix)를 찾아 반환하라. 만약 공통의 접두사가 없다면 빈 문자열("")을 반환하라.

입출력 예 1:
```
    Input: strs = ["flower","flow","flight"]
    Output: "fl"
```
입출력 예 2:
```
    Input: strs = ["dog","racecar","car"]
    Output: ""
    Explanation: There is no common prefix among the input strings.
```
---
풀이:     
1. 첫 번째 문자열을 기본 공통 접두사로 설정한다. 
2. 첫 번째 문자열부터 차례대로 다음 문자열들과 비교하면서 공통 접두사를 업데이트한다. 
3. 만약 현재 접두사가 해당 문자열에 없다면, 접두사의 마지막 문자를 제거하고 다시 비교를 진행한다. 
4. 모든 문자열을 검사한 후의 접두사를 반환한다.

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        String prefix = strs[0];
        
        for (int i=1; i<strs.length; i++) {
            while (strs[i].indexOf(prefix) != 0) {
                prefix = prefix.substring(0, prefix.length() - 1);
            }
        }
        
        return prefix;
    }
}
```

또 다른 풀이

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        String prefix = strs[0];
        
        for (int i=1; i<strs.length; i++) {
            while (!strs[i].startsWith(prefix)) {
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix.isEmpty()) return "";
            }
        }
        
        return prefix;
    }
}
```




### [LeetCode 121: Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/?envType=study-plan-v2&envId=top-interview-150)
문제 요구사항:        
주어진 가격 배열에서 한 번의 주식 구매와 판매로 얻을 수 있는 최대 이익을 반환하라. 이익을 얻을 수 없는 경우 0을 반환하라.

입출력 예 1:
```
    Input: prices = [7,1,5,3,6,4]
    Output: 5
```
입출력 예 2:
```
    Input: prices = [7,6,4,3,1]
    Output: 0
```
---
풀이:
1. 첫 번째 가격을 최소 가격으로 초기화한다. 
2. 배열을 순회하며 현재 가격이 이전의 최소 가격보다 작다면, 최소 가격을 업데이트한다. 
3. 현재 가격이 이전의 최소 가격보다 크다면, 현재 이익(현재 가격 - 최소 가격)을 계산하고, 이를 이전의 최대 이익과 비교하여 최대 이익을 업데이트한다. 
4. 모든 가격을 검사한 후의 최대 이익을 반환한다.

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = prices[0];
        int maxProfit = 0;
        
        for (int i=1; i<prices.length; i++) {
            if (minPrice > prices[i]) {
                minPrice = prices[i];
            } else {
                maxProfit = Math.max(maxProfit, prices[i] - minPrice);
            }
        }
		
        return maxProfit;
    }
}
```




### [LeetCode 392: Is Subsequence](https://leetcode.com/problems/is-subsequence/?envType=study-plan-v2&envId=top-interview-150)
문제 요구사항:        
문자열 s가 문자열 t의 부분 수열인지 확인하라. 부분 수열은 원래 문자열에서 몇몇 문자를 삭제하여 만들 수 있는 새 문자열이며, 남은 문자들의 상대적인 위치는 변하지 않아야 한다. (예: "ace"는 "abcde"의 부분 수열이지만, "aec"는 아니다.)

입출력 예 1:
```
    Input: s = "abc", t = "ahbgdc"
    Output: true
```
입출력 예 2:
```
    Input: s = "axc", t = "ahbgdc"
    Output: false
```
---
풀이:
1. 두 문자열 s와 t에 대한 인덱스를 설정한다. 
2. 문자열 s를 순회하며, 현재 문자가 문자열 t에서 일치하는 문자를 찾는다. 
3. 일치하는 문자를 찾으면, s의 다음 문자를 탐색한다. 
4. 문자열 t의 끝까지 도달하고도 일치하는 문자를 찾지 못하면 false를 반환한다. 
5. 모든 문자를 찾았다면 true를 반환한다.

메모:     
문자열의 부분 수열을 확인하는 문제에서는 **투 포인터 기법**을 사용하여 효율적으로 탐색할 수 있음을 알 수 있다. 이 방식은 두 문자열을 동시에 검사하면서 서로 일치하는 문자를 찾는 방식으로 작동하며, 이러한 접근 방법은 문자열 문제에서 유용하게 사용될 수 있다.

```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int indexInS = 0;
        int indexInT = 0;
        
        while (indexInS < s.length()) {
            if (indexInT == t.length()) return false;
            
            if (s.charAt(indexInS) == t.charAt(indexInT)) {
                indexInS++;
            }
            
            indexInT++;
        }
        
        return true;
    }
}
```




### [LeetCode 2: Add Two Numbers](https://leetcode.com/problems/add-two-numbers/?envType=study-plan-v2&envId=top-interview-150)
문제 요구사항:        
두 연결 리스트가 주어지며, 이 리스트들은 역순으로 저장된 자릿수를 통해 양의 정수를 나타낸다. 이 두 숫자를 더하고 그 합을 연결 리스트로 반환하라. 두 숫자는 0을 제외한 선행 0을 포함하지 않는다.

입출력 예 1:
```
    Input: l1 = [2,4,3], l2 = [5,6,4]
    Output: [7,0,8]
    Explanation: 342 + 465 = 807.
```
입출력 예 2:
```
    Input: l1 = [0], l2 = [0]
    Output: [0]
```
---
풀이:
1. 더미 노드를 사용하여 결과 연결 리스트를 초기화한다. 
2. 각 연결 리스트 노드를 순회하면서 두 숫자를 더하고, 이전의 캐리를 고려한다. 
3. 더한 값에서 10을 나눈 나머지를 현재 결과 노드의 값으로 설정한다. 
4. 더한 값이 10 이상일 경우 캐리 값을 설정한다. 
5. 모든 노드를 순회한 후에도 캐리 값이 남아있으면 결과 연결 리스트에 추가한다. 
6. 더미 노드의 다음 노드부터 결과를 반환한다.

메모:     
연결 리스트를 사용하는 문제에서는 **더미 노드(dummy node)**를 활용하면 코드의 복잡성을 줄일 수 있음을 알 수 있다. 또한, **캐리(carry)**를 사용하여 자릿수를 올릴 때의 처리 방법과 연결 리스트의 기본적인 순회와 조작 방법을 연습할 수 있다.

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;
        int carry = 0;
        
        while (l1 != null || l2 != null) {
            int a = (l1 != null) ? l1.val : 0;
            int b = (l2 != null) ? l2.val : 0;
            int sum = carry + a + b;
            
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;
            
            if (l1 != null) {
                l1 = l1.next;
            }
            if (l2 != null) {
                l2 = l2.next;
            }
        }
        
        if (carry > 0) {
            current.next = new ListNode(carry);
        }
    
        return dummy.next;
    }
}
```