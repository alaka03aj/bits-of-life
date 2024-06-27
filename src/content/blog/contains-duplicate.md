---
author: Alaka A J
pubDatetime: 2024-06-24T16:39:00+00:00
title: Contains Duplicate | LeetCode
slug: contains-duplicate
featured: true
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - leetcode
  - array
  - blind75
  - easy
  - dsa
  - hash
description: Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Problem Statement](#problem-statement)
- [Example](#example)
- [Think out loud:](#think-out-loud)
- [Conclusions](#conclusions)
- [Approach](#approach)
  - [Brute Force:](#brute-force)
  - [Using HashMap/HashSet:](#using-hashmaphashset)
- [Things to look into:](#things-to-look-into)
- [Alternatives:](#alternatives)

## Problem Statement

Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

## Example

```bash
Input: nums = [1,2,3,1]
Output: true

Input: nums = [1,2,3,4]
Output: false

Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

## Think out loud:

1. Not distinct
2. Not N-1 distinct elements

## Conclusions

1. Array can have any number with any number of frequencies.
2. We need to check whether the array has any duplicate elements or not.

## Approach

### Brute Force:

- For each element in the array, check if it exists in the array (excluding the current element).
- Pseudo Code:

  ```
  for i in A:
  	for j in A and j != i:
  		if i == j
  			return True
  return False
  ```

- Time Complexity: O(N^2), as both i is traversed n times and for each i, j is traversed n-1 times
- Space Complexity: O(1)

### Using HashMap/HashSet:

- If an entry occurs to hashmap/hashset such that the element is already present in it, then the current element is duplicate.
- Pseudo Code:
  ```
  hash = {}
  for i in A:
  	if i not in hash:
  		 hash[i] = 1
  	else:
  		return True
  return False
  ```
- Time Complexity: O(N)
- Space Complexity: O(N)

## Things to look into:

- Time taken to search in hash map/set

## Alternatives:

1. Sort array, linear traversal, check for adjacent duplicate elements [TC: O(n*logn) SC: O(1)]
2. Using ordered map and set [TC: O(n*logn) SC: O(n)]
