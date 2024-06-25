---
author: Alaka A J
pubDatetime: 2024-06-24T21:15:43.398481+05:30
title: Valid Anagram | LeetCode
slug: valid-anagram
featured: true
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - leetcode
  - array
  - blind75
  - easy
  - dsa
  - hash
description: Given two strings s and t, return true if t is an anagram of s, and false otherwise.
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
- [Follow Up](#follow-up)

## Problem Statement

Given two strings `s` and `t`, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Example

```bash
Input: s = "anagram", t = "nagaram"
Output: true

Input: s = "rat", t = "car"
Output: false
```

## Think out loud:

1. Can s be a subset of t?
2. t is an anagram of s means all the letters in s is present in t right?
3. Size of s and t are to be same?

## Conclusions

1. If size of t is not equal to s, not an anagram.
2. Else, check if all the letters in s are present in t.

## Approach

### Brute Force:

- For each character in s, check if it is present in t. If yes, replace that char in t with something else.
- Pseudo Code:

  ```

  ```

- Time Complexity: O(n^2)
- Space Complexity: O(1)

### Using HashMap/HashSet:

-
- Pseudo Code:

  ```

  ```

- Time Complexity: O(n)
- Space Complexity: O(n)

## Things to look into:

-

## Alternatives:

1.  [TC: O() SC: O()]
2.  [TC: O() SC: O()]

## Follow Up

What if the inputs contain unicode characters? How would you adapt your solution to such a case?

```bash
#include <iostream>
#include <unordered_map>
#include <string>

using namespace std;

bool isAnagram(const string& s, const string& t) {
    if (s.size() != t.size()) {
        return false;
    }

    unordered_map<char32_t, int> count_s, count_t;

    // Use UTF-8 to UTF-32 conversion to handle Unicode characters
    auto utf8_to_utf32 = [](const string& str) -> u32string {
        u32string result;
        char32_t codepoint = 0;
        int bytes_remaining = 0;

        for (unsigned char ch : str) {
            if (bytes_remaining == 0) {
                if (ch < 0x80) {
                    result += ch;
                } else if (ch < 0xE0) {
                    codepoint = ch & 0x1F;
                    bytes_remaining = 1;
                } else if (ch < 0xF0) {
                    codepoint = ch & 0x0F;
                    bytes_remaining = 2;
                } else {
                    codepoint = ch & 0x07;
                    bytes_remaining = 3;
                }
            } else {
                codepoint = (codepoint << 6) | (ch & 0x3F);
                bytes_remaining--;
                if (bytes_remaining == 0) {
                    result += codepoint;
                }
            }
        }

        return result;
    };

    u32string s32 = utf8_to_utf32(s);
    u32string t32 = utf8_to_utf32(t);

    for (char32_t ch : s32) {
        count_s[ch]++;
    }

    for (char32_t ch : t32) {
        count_t[ch]++;
    }

    return count_s == count_t;
}

int main() {
    string s1 = "anagram";
    string s2 = "nagaram";
    cout << boolalpha << isAnagram(s1, s2) << endl; // Output: true

    string s3 = "rat";
    string s4 = "car";
    cout << boolalpha << isAnagram(s3, s4) << endl; // Output: false

    // Test with Unicode characters
    string s5 = u8"안녕하세요";
    string s6 = u8"세요하녕안";
    cout << boolalpha << isAnagram(s5, s6) << endl; // Output: true

    return 0;
}
```
