---
layout: post
title: "Stack(Doubly Linked Lists로 구현)(python)"
tags:
  - [자료구조]
  - [python]
  - [양방향 연결 리스트]
  - [스택]
---

## 코드 구현

```python
# 이전에 작성한 Node, Doubly Linked List 클래스를 활용.
from dobuly import Node
from dobuly import DoublyLinkedList

class LinkedListStack:
    def __init__(self):
        self.data = DoublyLinkedList()

    def size(self):
        return self.data.getLength()

    def isEmpty(self):
        return self.size() == 0

    def push(self, item):
        node = Node(item)
        self.data.insertAt(self.size() + 1, node)

    def pop(self):
        self.data.popAt(self.size())

    def peek(self):
        return self.data.getAt(self.size()).data
```
