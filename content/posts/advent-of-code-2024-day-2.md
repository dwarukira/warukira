+++
date = '2024-12-04T10:06:55+03:00'
draft = false
title = 'Advent of Code 2024 Day 2'
+++

```python

# part one
from functools import reduce


reports = [x.split(" ") for x in input_str.split("\n")]
safe_count = 0

increasing = lambda x: reduce(lambda a, b: a and b, [x[i] < x[i + 1] for i in range(len(x) - 1)])
decreasing = lambda x: reduce(lambda a, b: a and b, [x[i] > x[i + 1] for i in range(len(x) - 1)])

for report in reports:
    if not increasing(report) and not decreasing(report):
        safe_count += 1

print(safe_count)

    
```