## [[LEET CODE JUNKY#Contains Duplicates|Contains Duplicates]]

1. It initializes an empty set `hashset` to keep track of the unique elements in the input list `nums`.

2. It then iterates over the elements in the input list `nums` using a for loop. For each element, it checks if it is already in the set `hashset`. If it is, it means that we have already encountered this element before, so it returns `True` because the input list contains a duplicate element.

3. If the element is not in the set `hashset`, it adds the element to the set using the `add` method.

4. If the function finishes iterating over the input list `nums` and does not find any duplicate elements, it returns `False` because the input list does not contain any duplicate elements.

Alternative 2
1) Use ``set(nums)``  removes duplicates from list
2) Check if their ``len()`` is equal to length of list
3) ``return len(set(nums))!=len(nums)``

## [[LEET CODE JUNKY#Valid Anagram|Valid Anagram]]

1. It first checks if the lengths of the two strings `s` and `t` are equal. If not, it returns `False` because it is impossible for the two strings to be anagrams of each other.

2. It then initializes two empty dictionaries `countS` and `countT` to keep track of the frequency of each character in the strings `s` and `t` respectively.

3. It then iterates over the characters in the strings `s` and `t` using a for loop. For each character, it increments the corresponding value in the `countS` and `countT` dictionaries. The `get` method is used to handle the case where the character is not already in the dictionary. If the character is not in the dictionary, `get` returns the default value of 0, which is then incremented by 1.

4. Finally, it compares the two dictionaries `countS` and `countT`  check if they are equal. If they are equal, it means that the two strings are anagrams of each other, so it returns `True`. Otherwise, it returns `False`.

## [[LEET CODE JUNKY#Two Sum|Two Sum]]

1. It initializes an empty dictionary `prevMap` to keep track of the values and their indices in the input list `nums`.

2. It then iterates over the input list `nums` using a for loop. For each number, it calculates the difference between the target integer `target` and the current number.

3. If the difference is already in the `prevMap` dictionary, it means that we have found two numbers that add up to the target integer, so it returns a list containing their indices.

4. If the difference is not in the `prevMap` dictionary, it adds the current number and its index to the `prevMap` dictionary.

5. If the function finishes iterating over the input list `nums` and does not find two numbers that add up to the target integer, it returns an empty list.

## [[LEET CODE JUNKY#Group Anagram|Group Anagram]]

1. It initializes an empty dictionary `dict_anagrams` to store the groups of anagrams.
    
2. It then iterates over the input list of strings `strs` using a for loop. For each string, it sorts the characters in the string and joins them together to create a key. This key will be used to group the anagrams together in the `dict_anagrams` dictionary.
    
3. If the key is already in the `dict_anagrams` dictionary, it means that we have already encountered an anagram of the current string, so it appends the current string to the list of anagrams for that key.
    
4. If the key is not in the `dict_anagrams` dictionary, it means that we have not encountered an anagram of the current string yet, so it creates a new list of anagrams for that key and adds the current string to it.
    
5. Finally, it returns a list of the values in the `dict_anagrams` dictionary, which now contains the groups of anagrams.

## [[LEET CODE JUNKY#Top K Frequent Elements|Top K Frequent Elements]]

1. It initializes an empty dictionary `frequency` to keep track of the frequency of each number in the input list `nums`.

2. It then iterates over the input list `nums` using a for loop. For each number, it increments the corresponding value in the `frequency` dictionary.

3. It then initializes an empty list `final` to store the `k` most frequent elements.

4. It then iterates `k` times using a for loop. In each iteration, it finds the key with the maximum value in the `frequency` dictionary using `max(frequency, key=frequency.get)`. It then adds the key to the `final` list and removes it from the `frequency` dictionary using `frequency.pop(maxkey)`.

5. Finally, it returns the `final` list, which now contains the `k` most frequent elements in the input list `nums`.

## [[LEET CODE JUNKY#Product of Array Except Self|Product of Array Except Self]]

1. It initializes a result list `res` with the same length as the input list `nums`, and fills it with 1s.

2. It then iterates over the input list `nums` from the second element to the last element. For each element, it multiplies the corresponding element in the result list `res` by the previous element in the input list `nums`. This step calculates the product of all the numbers to the left of the current index.

3. It initializes a variable `postfix` to 1. This variable will be used to calculate the product of all the numbers to the right of the current index.

4. It then iterates over the input list `nums` from the last element to the first element. For each element, it multiplies the corresponding element in the result list `res` by the `postfix` variable. Then it multiplies the `postfix` variable by the current element in the input list `nums`. This step calculates the product of all the numbers to the right of the current index.

5. Finally, it returns the result list `res`, which now contains the product of all the numbers in the input list except the number at the current index.


## [[LEET CODE JUNKY#Valid Sudoku|Valid Sudoku]]

1. It initializes three default dictionaries `cols`, `rows`, and `squares` to keep track of the unique elements in each column, row, and 3x3 subgrid of the input `board` respectively.

2. It then iterates over the elements in the input `board` using two nested for loops. For each element, it checks if it is a digit from 1 to 9 or a period (`.`), which represents an empty cell. If it is a period, it continues to the next iteration.

3. If the element is a digit from 1 to 9, it checks if it is already in the corresponding set in the `cols`, `rows`, and `squares` dictionaries. If it is, it means that we have already encountered this element in the same column, row, or 3x3 subgrid, so it returns `False` because the input `board` is not a valid Sudoku board.

4. If the element is not in the corresponding set in the `cols`, `rows`, and `squares` dictionaries, it adds the element to the set using the `add` method.

5. If the function finishes iterating over the input `board` and does not find any duplicate elements, it returns `True` because the input `board` is a valid Sudoku board.

## [[LEET CODE JUNKY#Longest Consecutive Sequence|Longest Consecutive Sequence]]

1. It initializes a set `numSet` with the elements in the input list `nums`. This allows for O(1) lookup time, which is faster than using a list.

2. It initializes a variable `longest` to 0 to keep track of the length of the longest consecutive subsequence.

3. It then iterates over the elements in the set `numSet` using a for loop. For each element, it checks if it is the start of a consecutive subsequence by checking if `(n - 1)` is not in the set `numSet`. If `(n - 1)` is not in the set, it means that `n` is the start of a consecutive subsequence.

4. If `n` is the start of a consecutive subsequence, it initializes a variable `length` to 1 and then enters a while loop that increments `length` by 1 for each consecutive number in the subsequence. The while loop continues as long as `(n + length)` is in the set `numSet`.

5. After the while loop, it updates the variable `longest` with the maximum of `length` and `longest`. This ensures that `longest` always contains the length of the longest consecutive subsequence found so far.

6. Finally, it returns the variable `longest`, which now contains the length of the longest consecutive subsequence in the input list `nums`.

