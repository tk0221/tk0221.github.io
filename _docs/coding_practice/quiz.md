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

## Medium

## Hard
