![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz033text.png)
Function
```.py
def mystery(list1, list2):
    output = []
    for i in range(len(list1)):
        for j in range(len(list2)):
            if list1[i] == list2[j]:
                output.append(list1[i])
    return output
```
Auto Testing
```.py
import pytest
from quiz33 import mystery

def test_empty_lists():
  assert mystery([], []) == []

def test_one_common_element():
  assert mystery([1, 2, 3], [3, 4, 5]) == [3]

def test_multiple_common_elements():
  assert mystery([1, 2, 3, 4], [3, 4, 5, 6]) == [3, 4]
```
1[](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz033test.jpeg)
