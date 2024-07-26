# Leet Code #1768: Merge Strings Alternately

<a href="https://leetcode.com/problems/merge-strings-alternately/description/">Link to problem</a>

## Problem
You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string

## Intuition
Think of the problem as two players with a set of cards and they take turns alternately playing one card at a time. Assume each player has an ordering to their cards and plays their cards in order. The result of all of their cards being played is the solution to our question.

## Approach

- Create two integers to keep track of the current index of each string
- Create a new empty string to store the result
- Iterate over both strings simultaneously using a while loop adding a single character from each string
- Finally if there is a mismatch in the string lengths, you add the remaining characters of the string with the longer length
- return result



## Time and Space complexities
### <strong>Time complexity:</strong> O(n)
We are iterating over both of the strings tracking each character. Since there are n characters in total, the time complexity is O(n)

### <strong>Space complexity:</strong> O(n)
We merge all of the characters into one string, therefore we have O(n) space complexity

## Code

### Python code

```Py
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        i = 0
        j = 0

        merged_word = ''

        while i < len(word1) and j < len(word2):
            merged_word += word1[i] + word2[j]
            i += 1
            j += 1

        if len(word1) > len(word2):
            merged_word += word1[i::]
        else:
            merged_word += word2[j::]

        return merged_word      
```

### Java code

```Java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        int i = 0;
        int j = 0;

        String merged_word = "";

        while (i < word1.length() && j < word2.length()) {
            merged_word = merged_word + word1.charAt(i) + word2.charAt(j);
            i++;
            j++;
        }

        while (i < word1.length()) {
            merged_word = merged_word + word1.charAt(i);
            i++;
        }

        while (j < word2.length()) {
            merged_word = merged_word + word2.charAt(j);
            j++;
        }

        return merged_word;
    }
}
```


### JavaScript code

```JS
/**
 * @param {string} word1
 * @param {string} word2
 * @return {string}
 */
var mergeAlternately = function(word1, word2) {
  let mergedWord = '';

  let i = 0;
  let j = 0;

  while (i < word1.length || j < word2.length) {
    if (i < word1.length) {
        mergedWord += word1[i];
        i++;
    }
    if (j < word2.length) {
        mergedWord += word2[j];
        j++;
    }
  }

  return mergedWord;
};
```

### C++ code

```cpp
class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        string mergedWord = "";
        int i = 0;
        int j = 0;

        while (i < word1.length() || j < word2.length()) {
            if (i < word1.length()) {
                mergedWord += word1[i]; 
                i++;
            }
            if (j < word2.length()) {
                mergedWord += word2[j];
                j++;
            }
        }

        return mergedWord;
    }
};
```

