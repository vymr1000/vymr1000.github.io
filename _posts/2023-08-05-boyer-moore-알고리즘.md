---
layout: post
category: 2023
---

Boyer-Moore 알고리즘은 배열 내에서 과반수 이상 등장하는 요소를 찾는데 사용되는 효율적인 알고리즘이다. 
배열 내에서 과반수를 차지하는 요소가 반드시 존재한다는 가정 하에 작동하며, 선형 시간 복잡도 O(n)와 상수 공간 복잡도 O(1)를 가진다.
이 알고리즘은 과반수 요소가 반드시 존재한다는 가정 하에서만 정확한 결과를 제공한다. 과반수 요소가 존재하지 않는 경우에는 추가적인 검증 단계가 필요할 수 있다.

```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        Integer candidate = null;
        
        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }
        return candidate;
    }
}
```