---
author: Alaka A J
pubDatetime: 2024-06-24T21:13:00+00:00
title: Template | LeetCode
slug: template-dsa
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - leetcode
  - array
  - a2z_dsa
  - easy
  - dsa
  - redo
description: Check whether the given array is sorted and rotated.
---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Problem Statement](#problem-statement)
- [Example](#example)
- [Think out loud:](#think-out-loud)
- [Conclusions](#conclusions)
- [Approach](#approach)
- [Things to look into:](#things-to-look-into)

## Problem Statement

Given an array `nums`, return true if the array was originally sorted in non-decreasing order, then rotated some number of positions (including zero). Otherwise, return `false`.

There may be duplicates in the original array.

Note: An array `A` rotated by `x` positions results in an array `B` of the same length such that `B[i] == A[(i+x) % A.length]` for every valid index i.

## Example

```bash
Input: nums = [3,4,5,1,2]
Output: true
Explanation: [1,2,3,4,5] is the original sorted array.
You can rotate the array by x = 3 positions to begin on the element of value 3: [3,4,5,1,2].

Input: nums = [2,1,3,4]
Output: false
Explanation: There is no sorted array once rotated that can make nums.

Input: nums = [1,2,3]
Output: true
Explanation: [1,2,3] is the original sorted array.
You can rotate the array by x = 0 positions (i.e. no rotation) to make nums.
```

## Think out loud:

1. There must be some link between each elements in a sorted and rotated array (peak and drops in a valley)
2. How to handle the case of rotation in an array?

## Conclusions

1. Consider the array as a circular one.
2. Use the concept of `B[i] == A[(i+x) % A.length]` to figure out if it is sorted or not.

## Approach

- Pseudo Code:

  ```
    bool check(vector<int>& nums) {
        int drop = 0;
        for (int i = 0; i < nums.size(); i++){
            if (nums[i] > nums[(i+1)%nums.size()]) {
                drop++;
                if (drop > 1) return false;
            }
        }

        return true;
    }
  ```

- Time Complexity: O(N)
- Space Complexity: O(1)

## Things to look into:

- Redo this question again
- Circular arrays and its operations
