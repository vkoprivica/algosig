---
title: Group Anagrams
category: AlgoSIG 1
link: https://leetcode.com/problems/group-anagrams/
author: Vukasin Koprivica
gh_comments_issue_id: 115
tags:
  - strings
---


## Description

Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Example

```python

strs = ["eat","tea","tan","ate","nat","bat"] # Input
[["bat"],["nat","tan"],["ate","eat","tea"]]  # Output

```

## Solution

```python
hash_values = dict()
results_dict = dict()

# Create the dictionary which each key is word and values is hash of the same word
for word in strs:
    hash_value = 0
    for letter in word:
        hash_value += hash(letter)
    hash_values[word] = hash_value

    # Create dictionary which keys are hash values and values are dictionary
    # with the words that have same hash_values
    if hash_value in results_dict:
        results_dict[hash_value].append(word)
    else:
        results_dict[hash_value] = [word]

# Return output in as a list
results = [v for v in results_dict.values()]
return results
```
