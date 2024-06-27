---
author: Alaka A J
pubDatetime: 2024-06-26T22:30:00+05:30
title: Climbing Stairs | LeetCode
slug: climbing-stairs
featured: true
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - leetcode
  - array
  - blind75
  - easy
  - dsa
  - dp
description: Different ways to reach the top of a staircase with n steps, where you can either climb 1 or 2 steps at a time.
---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Problem Statement](#problem-statement)
- [Example](#example)
- [Approach](#approach)
  - [Brute Force](#brute-force)
  - [Memoization](#memoization)
  - [Top Down Approach](#top-down-approach)
- [Things to look into](#things-to-look-into)

## Problem Statement

You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

## Example

```bash
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps

Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

## Approach

### Brute Force:

- Recursive approach of fibonacci series
- Pseudo Code:

  ```bash
  int climbStairs(int n) {
        if (n == 0 || n == 1)
            return 1;
        return climbStairs(n-1) + climbStairs(n-2);
  }
  ```

- Time Complexity: O(2^n)
- Space Complexity: O(n)

### Memoization:

- Bottom up approach of the recursive solution
- Pseudo Code:

  ```bash
  int climbStairs(int n, vector<int>& dp) {
        if (n == 0 || n == 1)
            return dp[n] = 1;
        if (dp[n] != 0)
            return dp[n];
        return dp[n] = climbStairs(n-1) + climbStairs(n-2);
  }
  ```

- Time Complexity: O(n)
- Space Complexity: O(n)

### Top Down Approach:

- Top down approach of the recursive solution
- We only need two variables to start 1 and 0
- Pseudo Code:

  ```bash
  int climbStairs(int n) {
        if (n == 0 || n == 1)
            return 1;
        int first = 1, second = 1, third;
        for (int i = 2; i <= n; i++) {
            third = first + second;
        }
  }
  ```

- Time Complexity: O(n)
- Space Complexity: O(1)

## Things to look into:

- How to turn a recursive solution to a top down approach.
- Identifying DP questions.
