# two sum  [hash tables]

video reference : https://www.youtube.com/watch?v=7jDS9KQEDbI

![[Pasted image 20250301000328.png]]

- whenever there is searching then there is sort 
- try to sort ele first in searching


```java
class Solution {

	public int[] twoSum(int[] nums, int target) {

		Map<Integer, Integer> map = new HashMap<>();
		for (int i = 0; i < nums.length; i++ ){

			int complement = target - nums[i];
			if(map.containsKey(complement)) {
				return new int[]{map.get(complement), i};
			}

			map.put(nums[i], i);
		}
		throw new IllegalArgumentException("No 2 sum found ");
	}

}
```