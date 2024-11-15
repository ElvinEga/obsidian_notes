---
tags: [leetcode, neetcode]
---
https://github.com/himalayadua/Neetcode-150/tree/main
contains languages
https://github.com/th-blitz/NeetCode-150
simple 
https://github.com/peterbonnesoeur/Neetcode150/tree/main
notes
https://github.com/siddharthroy12/Leetcode-Notes

Needcode master
https://github.com/neetcode-gh/leetcode/tree/main

Contains Duplicate
TS,JS
Python

# Arrays & Hashing

- [x] Contains Duplicates ✅ 2024-09-26
- [ ] Valid Anagram
- [ ] Two Sum
- [ ] Group Anagram
- [ ] To K Frequent Elements
- [ ] Product of Array Except Self
- [ ] Valid Sudoku
- [ ] Encode and Decode String
- [ ] Longest Consecutive Sequence


##  Contains Duplicates

Given an integer array `nums`, return `true` if any value appears **more than once** in the array, otherwise return `false`.

```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        hashset = set()
        for n in nums:
            if n in hashset:
                return True
            hashset.add(n)
        return False  


#Approach 2
from typing import List
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(set(nums))!=len(nums)


```

```js
class Solution {

/**
* @param {number[]} nums
* @return {boolean}
*/

hasDuplicate(nums) {

	const hashSet = new Set();

	for(const num of nums){

		if(hashSet.has(num)) return true;

		hashSet.add(num);

	}

return false;

	}
}
```

## Valid Anagram

Given two strings `s` and `t`, return `true` if the two strings are anagrams of each other, otherwise return `false`.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        for a in set(s):
            if s.count(a) != t.count(a):
                return False

        return True

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        countS, countT = {}, {}

        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)
        return countS == countT
```

```js
class Solution {
    /**
     * @param {string} s
     * @param {string} t
     * @return {boolean}
     */
    isAnagram(s, t) {
        if(s.length !== t.length) return false;

        let first = s.split('');
        const second = t.split('');

        for(let i = 0; i < second.length; i++){
            const element = second[i];
            let found = first.indexOf(element);
		            if (found !== -i){
                 first[found] = null;
            }else{
                return false;
            }
        }
        return true
    }
}

```

```ts
class Solution {
    isAnagram(s: string, t: string): boolean {
        if (s.length !== t.length) {
            return false;
        }

        const countS: {[key: string]: number} = {};
        const countT: {[key: string]: number} = {};

        for (let i = 0; i < s.length; i++) {
            countS[s[i]] = 1 + (countS[s[i]] || 0);
            countT[t[i]] = 1 + (countT[t[i]] || 0);
        }
        return JSON.stringify(countS) === JSON.stringify(countT);
    }
}

```
## Two Sum
Given an array of integers `nums` and an integer `target`, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.

You may assume that _every_ input has exactly one pair of indices `i` and `j` that satisfy the condition.

Return the answer with the smaller index first.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prevMap = {}  # val -> index

        for i, n in enumerate(nums):
            diff = target - n
            if diff in prevMap:
                return [prevMap[diff], i]
            prevMap[n] = i
```

```ts
function twoSum(nums: number[], target: number): number[] {
    let hash: { [key: number]: number } = {};
    for (let i = 0; i < nums.length; i++) {
        let diff = target - nums[i];
        if (diff in hash) {
            return [hash[diff], i];
        } else {
            hash[nums[i]] = i;
        }
    }
}

```

## Group Anagram
Given an array of strings `strs`, group all _anagrams_ together into sub-lists. You may return the output in **any order**.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: strs = ["act","pots","tops","cat","stop","hat"]

Output: [["hat"],["act", "cat"],["stop", "pots", "tops"]]
```

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        dict_anagrams = {}
        for item in strs:
            key = ''.join(sorted(item))

            if key in dict_anagrams:
                dict_anagrams[key].append(item)

            else:
                dict_anagrams[key] = [item]

        return list(dict_anagrams.values())

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        ans = collections.defaultdict(list)

        for s in strs:
            count = [0] * 26
            for c in s:
                count[ord(c) - ord("a")] += 1
            ans[tuple(count)].append(s)
        return ans.values()

        
```

```ts
class Solution {
    groupAnagrams(strs: string[]): string[][] {
        const dict_anagrams: {[key: string]: string[]} = {};
        for (const item of strs) {
            const key = item.split('').sort().join('');

            if (key in dict_anagrams) {
                dict_anagrams[key].push(item);
            } else {
                dict_anagrams[key] = [item];
            }
        }

        return Object.values(dict_anagrams);
    }
}

```
## Top K Frequent Elements
Given an integer array `nums` and an integer `k`, return *the* `k` *most frequent elements*. You may return the answer in **any order**.

#### Example 1:
**Input:** nums = [1,1,1,2,2,3], k = 2

**Output:** [1,2]

#### Example 2:
**Input:** nums = [1], k = 1

**Output:** [1]

#### Constraints:
-   `1 <= nums.length <= 10^5^`
-   `-10^4^ <= nums[i] <= 10^4^`
-   `k` is in the range `[1, the number of unique elements in the array]`.
-   It is **guaranteed** that the answer is **unique**.

> Follow up: Your algorithm's time complexity must be better than `O(n log n)`, where n is the array's size.

```python

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        frequency = {}
        for s in nums:
            frequency[s] = frequency.get(s, 0) + 1
        
        #new_nums = {k: v for k, v in sorted(frequency.items(), key=lambda item: item[1])}

        final = []
        for i in range(k):
            #final.append(x.keys().index("c"))
            #max(frequency.values()) -- max value

            #key with max value -- max(frequency, key=frequency.get)
            maxkey = max(frequency, key=frequency.get)
            final.append(maxkey)
            frequency.pop(maxkey)

        return final
```

```ts
class Solution {
    topKFrequent(nums: number[], k: number): number[] {
        const frequency: {[key: number]: number} = {};
        for (const s of nums) {
            frequency[s] = (frequency[s] || 0) + 1;
        }

        const final: number[] = [];
        for (let i = 0; i < k; i++) {
            const maxkey = Object.keys(frequency).reduce((a, b) => frequency[+a] > frequency[+b] ? a : b);
            final.push(+maxkey);
            delete frequency[+maxkey];
        }

        return final;
    }
}

class Solution {
    topKFrequent(nums, k) {
        const frequency = {};
        for (const s of nums) {
            frequency[s] = (frequency[s] || 0) + 1;
        }

        const final = [];
        for (let i = 0; i < k; i++) {
            const maxkey = Object.keys(frequency).reduce((a, b) => frequency[+a] > frequency[+b] ? a : b);
            final.push(+maxkey);
            delete frequency[+maxkey];
        }

        return final;
    }
}


```
## Product of Array Except Self
Given an integer array `nums`, return *an array* `answer` *such that* `answer[i]` *is equal to the product of all the elements of* `nums` *except* `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**

**Input:** nums = [1,2,3,4]
**Output:** [24,12,8,6]

**Example 2:**

**Input:** nums = [-1,1,0,-3,3]
**Output:** [0,0,9,0,0]

**Constraints:**

-   `2 <= nums.length <= 10^5^`
-   `-30 <= nums[i] <= 30`
-   The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.


```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        res = [1] * (len(nums))

        for i in range(1, len(nums)):
            res[i] = res[i-1] * nums[i-1]
        postfix = 1
        for i in range(len(nums) - 1, -1, -1):
            res[i] *= postfix
            postfix *= nums[i]
        return res

```


```js
class Solution {
    productExceptSelf(nums: number[]): number[] {
        let res = Array(nums.length).fill(1);

        for (let i = 1; i < nums.length; i++) {
            res[i] = res[i - 1] * nums[i - 1];
        }
        let postfix = 1;
        for (let i = nums.length - 1; i >= 0; i--) {
            res[i] *= postfix;
            postfix *= nums[i];
        }
        return res;
    }
}

```


## Valid Sudoku

You are given a a `9 x 9` Sudoku board `board`. A Sudoku board is valid if the following rules are followed:

1. Each row must contain the digits `1-9` without duplicates.
2. Each column must contain the digits `1-9` without duplicates.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without duplicates.

Return `true` if the Sudoku board is valid, otherwise return `false`

Note: A board does not need to be full or be solvable to be valid.

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        cols = collections.defaultdict(set)
        rows = collections.defaultdict(set)
        squares = collections.defaultdict(set)  # key = (r /3, c /3)

        for r in range(9):
            for c in range(9):
                if board[r][c] == ".":
                    continue
                if (
                    board[r][c] in rows[r]
                    or board[r][c] in cols[c]
                    or board[r][c] in squares[(r // 3, c // 3)]
                ):
                    return False
                cols[c].add(board[r][c])
                rows[r].add(board[r][c])
                squares[(r // 3, c // 3)].add(board[r][c])

        return True

```

## Longest Consecutive Sequence

Given an array of integers `nums`, return _the length_ of the longest consecutive sequence of elements.

A _consecutive sequence_ is a sequence of elements in which each element is exactly `1` greater than the previous element.

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

```java
Input: nums = [2,20,4,10,3,4,5]

Output: 4
```

Explanation: The longest consecutive sequence is `[2, 3, 4, 5]`.

**Example 2:**

```java
Input: nums = [0,3,2,5,4,6,1,1]

Output: 7
```

**Constraints:**

- `0 <= nums.length <= 1000`
- `-10^9 <= nums[i] <= 10^9`

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        numSet = set(nums)
        longest = 0

        for n in numSet:
            # check if its the start of a sequence
            if (n - 1) not in numSet:
                length = 1
                while (n + length) in numSet:
                    length += 1
                longest = max(length, longest)
        return longest
```


# Two Pointers

- [ ] Valid Palindrome
- [ ] Two Sum II Input Array is Sorted
- [ ] 3Sum Container with Most Water
- [ ] Trapping Rain Water

## Valid Palindrome

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` *if it is a **palindrome**, or* `false` *otherwise*.

**Example 1:**
**Input:** s = "A man, a plan, a canal: Panama"

**Output:** true

**Explanation:** "amanaplanacanalpanama" is a palindrome.

**Example 2:**
**Input:** s = "race a car"

**Output:** false

**Explanation:** "raceacar" is not a palindrome.

**Example 3:**
**Input:** s = " "

**Output:** true

**Explanation:** s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

**Constraints:**

-   `1 <= s.length <= 2 * 10^5^`
-   `s` consists only of printable ASCII characters.

```python

# Approach 1:
class Solution:
    def isPalindrome(self, s: str) -> bool:
        new = ''
        for a in s:
            if a.isalpha() or a.isdigit():
                new += a.lower()
        return (new == new[::-1])

class Solution:
    def isPalindrome(self, s: str) -> bool:
        new = ''
        for c in s:
            if a.isalnum:
                new += c.lower()
        return (new == new[::-1])


# Approach 2: without extra memory
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s) - 1
        while r < l:
            while l < r and not s[l].isalnum(): l += 1
            while l < r and not s[r].isalnum(): r -= 1

            if s[l].lower() != s[r].lower(): return False
            l += 1
            r -= 1

        return True

def alphaNum(self, c):
return (ord('A') <= ord(c) <= ord('Z') or
		 ord('a') <= ord(c) <= ord('z') or
		 ord('0') <= ord(c) <= ord('9'))

```



## 3Sum
Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

**Input:** nums = [-1,0,1,2,-1,-4]
**Output:** [[-1,-1,2],[-1,0,1]]
**Explanation:**
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.

**Example 2:**

**Input:** nums = [0,1,1]
**Output:** []
**Explanation:** The only possible triplet does not sum up to 0.

**Example 3:**

**Input:** nums = [0,0,0]
**Output:** [[0,0,0]]
**Explanation:** The only possible triplet sums up to 0.

**Constraints:**

-   `3 <= nums.length <= 3000`
-   `-10^5^ <= nums[i] <= 10^5^`


> Hint 1
>> So, we essentially need to find three numbers x, y, and z such that they add up to the given value. If we fix one of the numbers say x, we are left with the two-sum problem at hand!
* * * * *

> Hint 2
>> For the two-sum problem, if we fix one of the numbers, say x, we have to scan the entire array to find the next number y, which is value - x where value is the input parameter. Can we change our array somehow so that this search becomes faster?
* * * * *

> Hint 3
>> The second train of thought for two-sum is, without changing the array, can we use additional space somehow? Like maybe a hash map to speed up the search?
* * * * *