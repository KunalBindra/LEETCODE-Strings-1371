# LEETCODE-Strings-1371
The problem this code is solving is about finding the longest substring of a given string `s` where all vowels (`a`, `e`, `i`, `o`, `u`) occur an even number of times. Let's walk through the dry run of this code with a sample input string to better understand how it works.

### Input:
Let's take an example string `s = "eleetminicoworoep"`.

### Dry Run:

1. **Initial setup**:
   - `mp`: A map to store the first occurrence of each vowel state combination. It starts with `{ "00000": -1 }`, which represents the state when no vowels have been encountered.
   - `vol`: An array of size 5 initialized to `[0, 0, 0, 0, 0]`, where each index corresponds to a vowel (`a`, `e`, `i`, `o`, `u`).
   - `currs`: A string representing the current vowel state as a binary string. It starts with `"00000"`, indicating that all vowels have been encountered an even number of times.
   - `maxlength`: Keeps track of the longest substring with all vowels appearing an even number of times.

2. **Iteration over the string**:
   
   For each character in the string, the code updates the vowel count and checks whether the current vowel state has been encountered before.

   - **Index 0, character: 'e'**:
     - Vowel 'e' is encountered, so `vol[1]` is toggled from 0 to 1.
     - `currs` becomes `"01000"`.
     - This state hasn't been encountered before, so we store it in the map: `mp = { "00000": -1, "01000": 0 }`.

   - **Index 1, character: 'l'**:
     - 'l' is not a vowel, so `vol` remains unchanged.
     - `currs` stays `"01000"`.
     - This state has been seen at index 0, so the longest substring ending here is `1 - 0 = 1`.

   - **Index 2, character: 'e'**:
     - Vowel 'e' is encountered again, so `vol[1]` is toggled back to 0.
     - `currs` becomes `"00000"`.
     - This state was initially seen at index -1, so the longest substring ending here is `2 - (-1) = 3`. Update `maxlength = 3`.

   - **Index 3, character: 'e'**:
     - Vowel 'e' is toggled again to make `vol[1] = 1`.
     - `currs` becomes `"01000"`.
     - This state was seen at index 0, so the longest substring ending here is `3 - 0 = 3`. `maxlength` remains 3.

   - **Continue similarly for the rest of the string**...

   - **Final calculation**:
     After processing the entire string, the algorithm returns the value of `maxlength`, which holds the length of the longest substring where all vowels appear an even number of times.

### Final Output:
For the input string `"eleetminicoworoep"`, the algorithm would return `13` as the length of the longest valid substring.

This approach runs in O(n) time, where `n` is the length of the string, since it processes each character once and uses a hash map to store and lookup states efficiently.
