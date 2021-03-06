---
layout: post
title: "Valid Palindrome(python)"
tags:
  - [algorithm]
  - [leetcode]
  - [완전 탐색]
  - [정규 표현식]
  - [투 포인터]
  - [python]
---

## 참고 자료

---

파이썬 알고리즘 인터뷰  
[leetcode - Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

## 문제

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.  
**Note:** For the purpose of this problem, we define empty string as valid palindrome.

**Example 1:**

```python
Input: "A man, a plan, a canal: Panama"
Output: true
```

**Example 2:**

```python
Input: "race a car"
Output: false
```

**Constraints:**

- s consists only of printable ASCII characters.

## palindrome(팰린드롬)이란

앞뒤가 똑같은 단어나 문장으로, 뒤집어도 같은 말이 되는 단어 또는 문장을 의미한다.

## 나의 생각

정규 표현식을 통해서 알파벳만을 리스트에 담아야겠다고 생각했다.  
그리고 비교는 slicing을 이용해서 거꾸로의 리스트와 비교해야겠다고 생각했다.

## 코드

- 정규 표현식 사용.  
   비교는 리스트 자체를 비교.

```python
import re
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.lower()
        s = re.sub("[^a-z0-9]", "", s)

        return s == s[::-1]
```

- isalnum() 함수를 사용.(글자 또는 숫자인지 확인)

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        answer = True
        str_list = [i.lower() for i in s if i.isalnum()]
        for i, j in zip(str_list, str_list[::-1]):
            if i != j:
                answer = False
        return answer
```

- Deque를 사용.
  비교는 pop()을 사용해서 비교

```python
import collections

class Solution:
    def isPalindrome(self, s: str) -> bool:
        strs = collections.deque()

        for char in s:
            if char.isalnum():
                strs.append(char.lower())

        while len(strs) > 1:
            if strs.popleft() != strs.pop():
                return False

        return True
```

- 투 포인터 사용.(Reverse String을 보고 투 포인터로 접근)

```python
import re

class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.lower()
        s = re.sub("[^0-9a-z]", "", s)
        left, right = 0, len(s) - 1
        while left < right:
            if s[left] != s[right]:
                return False
            left += 1
            right -= 1
        return True
```
