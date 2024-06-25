---
author: Alaka A J
pubDatetime: 2024-06-25T13:23:42.398481+05:30
title: Two Sum | LeetCode
slug: two-sum
featured: true
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - leetcode
  - array
  - blind75
  - easy
  - dsa
  - hash
description: Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Problem Statement](#problem-statement)
- [Example](#example)
- [Think out loud:](#think-out-loud)
- [Conclusions](#conclusions)
- [Approach](#approach)
  - [Brute Force:](#brute-force)
  - [Using HashMap (Two Pass):](#using-hashmap-two-pass)
  - [Using HashMap (One Pass):](#using-hashmap-one-pass)
- [Things to look into:](#things-to-look-into)
- [Alternatives:](#alternatives)

## Problem Statement

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

## Example

```bash
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

Input: nums = [3,2,4], target = 6
Output: [1,2]

Input: nums = [3,3], target = 6
Output: [0,1]
```

## Think out loud:

1. Are the elements distinct?
2. Will there be negative numbers?

## Conclusions

1. Elements aren't distinct
2. Negative numbers can be present

## Approach

### Brute Force:

- For each element in the array, check whether target - nums[i] is present in the array.
- Pseudo Code:

  ```bash
  for i in range(n):
      num2 = target - nums[i]
  for j in range(n):
      if num2 == nums[j] and i!=j:
      return {i, j}
  ```

- Time Complexity: O(n^2)
- Space Complexity: O(1)

### Using HashMap (Two Pass):

- In first pass, add all elements to hashmap. In the second pass, perform lookup.
- Pseudo Code:

  ```bash
  for i in range(n):
      hash[nums[i]] = i
  for i in range(n):
      num2 = target - nums[i]
      if num2 in hash and hash[num2]!=i:
          return {i, hash[num2]}
  ```

- Time Complexity: O(N)
- Space Complexity: O(N)

### Using HashMap (One Pass):

- Chech if `num2` exist in hash before adding the current element.
- Pseudo Code:

  ```bash
  for i in range(n):
      num2 = target - nums[i]
      if num2 in hash and hash[num2]!=i:
          return {i, hash[num2]}
      hash[nums[i]] = i
  ```

- Time Complexity: O(N)
- Space Complexity: O(N)

## Things to look into:

- Implementations of HashMap (Internal structure)
- Implementations of Binary Search
- mid = left + (right - left)/2 (to prevent integer overflow)

## Alternatives:

1. One Pass HashMap [TC: O(N) SC: O(N)]

## Bonus

Return true if a pair exists and false otherwise.

- Use linear traversal + binary search + hash [TC: O(n*logn) SC: O(n)]
