+++
date = '2024-12-04T11:40:32+03:00'
draft = true
title = 'Advent of Code 2024'
+++


### Day One

```python
input_str = open('input1.txt').read().strip()

# part one
list_one, list_two = zip(*(map(int, line.split("   ")) 
    for line in input_str.split("\n"))
)


s = sum(
    abs(a - b) for a, b in zip(
        sorted(list_one), 
        sorted(list_two))
)
print(s)

# part two

import collections
counter = collections.Counter(list_two)
similarity = sum([x * counter[x] for x in list_one if x in counter])
print(similarity)

```
