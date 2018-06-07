---
permalink: /docs/coding_practice/interviews/
title: "Coding Interviews"
toc: true
layout: single
---

## Easy

### Encode String [repl](https://repl.it/@tk0221/encode)
```ruby
#  Input : "aaabbbbdcal"  
#  Output : "a3b4d1c1a1l1"
def encode(str)
    res, cnt = "", 1
    (1..str.size).each do |i|
        if str[i-1] != str[i]
            res << str[i-1] + cnt.to_s
            cnt = 1
        else
            cnt+=1
        end
    end
    return res
end
testcases = ["", "a", "aa", "abc", "aaabbbbdcal"]
testcases.each { |str| pp encode(str) } # "", "a1", "a2", "a1b1c1", "a3b4d1c1a1l1"
```

### Sort array has only [0,1,2]  [repl](https://repl.it/@tk0221/sort1)
```ruby
#  Input : [1,2,0,1,2,0,1,1,1,0,0]
#  Output : [0, 0, 0, 0, 1, 1, 1, 1, 1, 2, 2]
#  note: input only contains 0,1,2 only

def sol1(nums)
    nums.sort #O(nlogn) which is not what we are looking for here
end

# Since we know input is only with 0,1,2 

def sol2(nums)
    zero, one, two = 0, 0, 0
    nums.each { |n| zero+=1 if n==0; one+=1 if n==1; two+=1 if n==2;}
    [0]*zero + [1]*one + [2]*two
end

# Faster than `sol1` we can print in nums to save memeory
# O(n) with O(1) memory which is `zero, one, two`

def sol3(nums)
    i, j = 0, 0
    (0...nums.size).each do |k|
        tmp = nums[k]
        nums[k] = 2
        if tmp < 2
            nums[i] = 1
            i+=1
        end
        if tmp == 0 
            nums[j] = 0
            j+=1
        end
    end
    nums
end

# while read each num, copy to `tmp`
# using i,j pointer to point 0's and 1's 
# i, j increasing when nums is 0
# O(n) with O(1) memory
```

## Medium

### Search k in array  [repl](https://repl.it/@tk0221/bsearch)
```ruby
# Req. search k in array and return true or false
# 1. array is unsorted   => [1,5,2,4,3]
# 2. array is sorted     => [1,2,3,4,5]
# 3. array is sorted but pivoted => [3,4,5,1,2]

def sol1(nums, k) #unsorted array
    nums.include?(k)
end
# need to run thru array
# O(n)

def sol2(nums, k) #sorted array
    lo, hi = 0, nums.size-1
    while lo <= hi do
        mid = (lo+hi)/2
        if k == nums[mid]
            return true
        elsif k < nums[mid]
            hi = mid - 1
        else
            lo = mid + 1
        end
    end
    return false
end
#search O(lg n) since each step we remove half of array

pp sol2([], 1) #test empty case 
pp sol2([1], 1)
pp sol2([1], 0)
pp sol2([0,1], 1)
pp sol2([1,2], 0)
pp sol2([1,2], 3)
pp sol2([1,2,3], 3)
pp sol2([1,2,3,5], 4)
```

## Hard
