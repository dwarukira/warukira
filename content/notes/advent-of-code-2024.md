+++
date = '2024-12-04T11:40:32+03:00'
draft = false
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


### Day two
```python

input_str = open('input2.txt').read().splitlines()

# part one
is_safe = lambda levels: all(
    (1 <= abs(a - b) <= 3) and ((a - b >= 0) == (levels[0] - levels[1] >= 0))
    for a, b in zip(levels, levels[1:])
)


safe_count = sum(is_safe([int(x) for x in line.split()]) for line in input_str)    
print(safe_count)

# part two
def safe_count_part_2():
    s_c = 0
    for report in input_str:
        levels = [int(x) for x in report.split()]
        if is_safe(levels):
            s_c += 1
        else:
            for i in range(len(levels)):
                if is_safe(levels[:i] + levels[i + 1 :]):
                    s_c += 1
    return s_c

print(safe_count_part_2)

```