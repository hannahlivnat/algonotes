# Cyclic Sort

### Definition

A coding pattern useful to solving problems involving arrays containing numbers in a given range to find missing or duplicate numbers

### Associated Time / Space Complexity
Should run in linear runtime complexity and constant space complexity

### When to Use
When you have a linear data structure such as an array and are asked to find the missing or duplicate number

### Common Operations / Implementation

```
Given an array containing n numbers from 0 ... n, find the missing number

input: [3, 0, 1]

def findMissingNumber(nums: number[]): number {
  let start = 0;

  while (start < nums.length) {
    const num = num[start];

    if (num < nums.length && num != start) {
      let temp = nums[start];
      nums[start] = nums[num];
      nums[num] = temp;
    } else {
      start++;
    }
  }

  for (let i = 0; i < nums.length; i++) {
    if (nums[i] != i) return i;
  }

  return len(nums);
}

Give an array containing nums in a range [1, n] and each int appears once or twice, return an array of all ints that appear twice

input = [1, 1, 2]

function findDuplicates(nums: number[]): number[] {
    let duplicates = [];
    
    for (let i = 0; i < nums.length; i++) {
        const num = Math.abs(nums[i]);

        if (nums[num - 1] < 0) {
            duplicates.push(num);
        } else {
            nums[num - 1] = -nums[num - 1];
        }
    }
    
    return duplicates;
};

```

### Resource Links
* [link](https://linkexamples.com)

