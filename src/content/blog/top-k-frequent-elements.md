---
author: Alaka A J
pubDatetime: 2024-06-25T21:14:00+00:00
title: Top K Frequent Elements | LeetCode
slug: top-k-frequent-elements
featured: true
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - leetcode
  - array
  - hash
  - heap
  - bucket-sort
  - blind75
  - medium
  - dsa
  - solo
  - redo
description: Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.
---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Problem Statement](#problem-statement)
- [Example](#example)
- [Think out loud](#think-out-loud)
- [Conclusions](#conclusions)
- [Approach](#approach)
  - [Brute Force](#brute-force-)
  - [Using Heap](#using-heap)
- [Things to look into](#things-to-look-into)
- [Alternatives](#alternatives)
  - [Using Bucket Sort](#using-bucket-sort)
- [Final Thoughts](#final-thoughts)

## Problem Statement

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements. You may return the answer in any order.

## Example

```bash
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]

Input: nums = [1], k = 1
Output: [1]
```

## Think out loud

1. Will value of k be greater than size of nums?

## Conclusions

1. If value of k is larger than size of nums, return {} (this never happens as the constraint for k is that k is [1, num(unique numbers in nums)]
2. Question was not what I thought it was. (here after submitting my brute force approach and getting a wrong answer instead of tle!)
   - We need to return the top k most frequent elements ie, their frequency must be in the top k
   ```bash
   Input: nums = [1,2], k = 2
   Output: [1,2]
   ```
   - This led me to think about heaps. (and we were right!)
3. If value of k and size of nums are same, return nums.

## Approach

### Brute Force

1. Version - 1 (Didn't pass all TC)

- Linear traversal + Linear Search + Store frequency to another array/hash + Traverse hash to print result
- Pseudo Code:
  ```bash
    1. Add frequency to hash.
    2. If value > k, print key.
  ```

2. Version - 2

- Pseudo Code:

  ```bash
    1. Add frequency to hash table.
    2. Sort them based on value.
    3. Print the top k elements.
  ```

- Time Complexity: O(n\*logn)
- Space Complexity: O(n+k)

### Using Heap

- Pseudo Code:

  ```bash
    1. Store frequencies to a hash table.
    2. Using the value of hash table as the priority for the heap, create a heap.
    3. Push all the keys to the heap.
    4. Pop the k keys from the heap and store it to the result vector.
    5. Return the vector.
  ```

- Time Complexity: O(k\*logn)
- Space Complexity: O(n)

## Things to look into

- Implementation of heap
- Min heap, max heap
- Different factors given for priorities
- Understand more about 2D vectors

## Alternatives

### Using Bucket Sort

- Pseudo Code:

  ```bash
    1. Store frequencies to a hash table.
    2. Using the value of hash table, create a 2D vector bucket[count][value].
    3. Populate the bucket using hash table.
    4. Starting from the last index of bucket, traverse and push elements to result vector till we get k elements.
    5. Return the vector.
  ```

- Time Complexity: O(n)
- Space Complexity: O(n)

## Final Thoughts

1. I really thought this this could be solved using linear search and hash table (brute force). But, I was sooo wrong.
2. We should always read the question and try to understand more examples before getting into coding.
3. I'm happy that we did think about implementing this question with heaps and this has made me believe that I'm improving and my brain is learning.
4. Never have I ever thought Bucket Sort can be used for this!
5. It seems like we know the logic, but we're either not fully confident to write the code or we don't know the syntax to implement it.
