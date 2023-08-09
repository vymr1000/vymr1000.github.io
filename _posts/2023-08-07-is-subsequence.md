---
layout: post
category: 2023
---

### 문제 
두 개의 문자열과 t가 주어지면 s가 t의 연속이면 true를 반환하고, 그렇지 않으면 false를 반환합니다.
문자열의 Subsequence은 나머지 문자의 상대적 위치를 방해하지 않고 문자 중 일부(없음)를 삭제하여 원래 문자열에서 형성되는 새로운 문자열입니다. (즉, "ace"는 "abcde"의 Subsequence은인 반면 "aec"은 그렇지 않습니다.).

입출력의 예 1:
```java
Input: s = "abc", t = "ahbgdc"
Output: true
``` 

입출력의 예 2:
```java
Input: s = "axc", t = "ahbgdc"
Output: false
```   
        
        
풀이
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int indexInS = 0;
        int indexInT = 0;
        
        // Iterate through string s
        while (indexInS < s.length()) {
            // If indexInT reaches the end of string t, return false
            if (indexInT == t.length()) return false;
            
            // If the characters match, move to the next character in string s
            if (s.charAt(indexInS) == t.charAt(indexInT)) {
                indexInS++;
            }
            
            // Move to the next character in string t
            indexInT++;
        }
        
        return true;
    }
}
```