---
permalink: /docs/coding_practice/intro/
title: "Coding practice with Ruby"
sidebar:
  nav: coding_practice
toc: true
layout: single
---

# Introduction

```ruby
"Hello, World!"
#>>"Hello, World!"
def f
  p "Hello, World!"
end
f
#>>"Hello, World!"
```
## Helpful Syntax

parallel swap
```ruby
a, b = 1, 2
a, b = b, a
#p [a, b] => 2, 1
```

## Basic Algorithm

### Sorting

#### Quick Sort [repl](https://repl.it/@tk0221/qsort)

```ruby
def partition(arr, lo, hi)
    piv = arr[hi]
    i = lo
    (lo...hi).each do |j|
        if arr[j] <= piv
            arr[i], arr[j] = arr[j], arr[i]
            i+=1
        end
    end
    arr[i], arr[hi] = arr[hi], arr[i]
    return i 
end 

def qsort(arr, lo=0, hi=arr.size-1)
    if lo < hi
        p = partition(arr, lo, hi)
        qsort(arr, lo, p-1)
        qsort(arr, p+1, hi)
    end
    arr
end
p qsort([])
p qsort([4,2,3,1,5,6,7,234,3,2,1,3])
```
