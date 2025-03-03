# two sum  [hash tables]

video reference : https://www.youtube.com/watch?v=7jDS9KQEDbI

![[Pasted image 20250301000328.png]]

- whenever there is searching then there is sort 
- try to sort ele first in searching (for bruteforce method)


```java
class Solution {

	public int[] twoSum(int[] nums, int target) {

		Map<Integer, Integer> map = new HashMap<>();
		for (int i = 0; i < nums.length; i++ ){

			int complement = target - nums[i];
			// Check if complement exists in `map`
			if(map.containsKey(complement)) {
				return new int[]{map.get(complement), i};
			}
			// Store the current number in `map`
			map.put(nums[i], i);
		}
		throw new IllegalArgumentException("No 2 sum found ");
	}
}
```

![[Pasted image 20250302140941.png]]

---

# Contain Duplicates: [[Hash SET]]
Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.



![[Pasted image 20250302152620.png]]


```java
class Solution {

	public boolean containsDuplicate(int[] nums) {
	// Create the hashset to store integers
		Set<Integer> intSet = new HashSet<>();
		// Iterate over each element
		for (int num : nums) {
			// Check if num is present in hashset
			if (intSet.contains(num))
				return true;
			// Add the num in hashset
			intSet.add(num);
		}
		return false;
		}
	}
```

---

# Valid Anagram:
leetcode 242:

with HashMap

```python
class Solution:
	def isAnagram(self, s: str, t: str) -> bool:
		if len(s) != len(t):
			return False
		countS,countT = {}, {}
		for i in range(len(s)):
			countS[s[i]] = 1 + countS.get(s[i], 0)
			countT[t[i]] = 1 + countT.get(t[i], 0)
		for c in countS:
			if countS[c] != countT.get(c, 0):
				return False
		return True
```

with sorting:

```python
class Solution: 
	def isAnagram(self, s: str, t: str) -> bool: 
		sorted_s = sorted(s) 
		sorted_t = sorted(t) 
		return sorted_s == sorted_t
```


