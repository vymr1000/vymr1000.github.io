---
layout: post
category: 2023
---

첫 번째 문자열을 초기 접두사로 설정한다. 이것이 공통 접두사가 될 가능성이 있는 문자열이다.
배열의 나머지 문자열들을 순회하면서, 현재 접두사가 해당 문자열의 접두사인지 확인한다.
현재 접두사가 문자열의 접두사가 아니라면, 접두사의 마지막 문자를 제거하여 접두사를 수축시킨다. 
이 작업을 해당 문자열이 접두사로 시작할 때까지 반복한다.


```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        String prefix = strs[0];
        
        for (int i=1; i<strs.length; i++) {
            while (strs[i].indexOf(prefix) != 0) {
                prefix = prefix.substring(0, prefix.length()-1);
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