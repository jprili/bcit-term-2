7 legged lie
6, 8 always said the truth

claims:
A -> 28 legs 7 + 7 + 7 + 7, 
B -> 27 legs 7 + 7 + 7 + 6
C -> 26 legs 7 + 7 + 6 + 6
D -> 25 legs 7 + 6 + 6 + 6

---

Find the longest common prefix string amongst an array of strings, if there's no common prefix, return an empty string.

```py

def longest_common_prefix(words: list[str]) -> str:
    if len(words) == 1:
        return words[0]

    prefix = ""
    word_index = 0
    shortest_word_length = min([len(word) for word in words])
    shortest_word = 
    while word_index < shortest_word_length:
        for index, word in enumerate(words):
            if index == 0:
            ...

SOLUTION:
# sort and compare the first and last
```
---
Remove Duplicates from sorted array

```py
def remove_duplicates(arr: list[int]) -> list[int]:
    if len(arr) == 1:
        return arr

    to_return = []
    number_so_far = None
    for number in arr:
        if number != number_so_far:
            to_return.append(number)
            number_so_far = number

    return to_return

```
