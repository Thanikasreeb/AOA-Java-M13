
# EX 3C Tug of War problem - Backtracking.
## DATE:
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
## 1.Compute Total Sum
Traverse the array and calculate the total sum of all elements.
If the total sum is odd, return false immediately (cannot split into two equal subsets).
## 2.Determine Target Subset Sum
Compute subSetSum = totalSum / 2.
This is the value each subset must sum to for a valid partition.
## 3.Initialize DP Array
Create a boolean array dp[subSetSum + 1] where dp[j] indicates whether a subset with sum j is possible.
Set dp[0] = true (zero sum is always achievable).
## 4.Fill DP Using Each Number
For each number in the array:
Iterate backwards from subSetSum down to the current number, updating:
dp[j] = dp[j] || dp[j - curr].
## 5.Return Result
After processing all numbers, return the value of dp[subSetSum],
which indicates whether an equal-sum partition is possible.

## Program:
```
/*
Program to implement Reverse a String
Developed by: Thanika Sree B
Register Number: 212222100055 
*/

import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        if (nums.length == 0)
            return false;
        int totalSum = 0;
        for (int num : nums) {
            totalSum += num;
        }
        if (totalSum % 2 != 0)
            return false;
        int subSetSum = totalSum / 2;
        boolean[] dp = new boolean[subSetSum + 1];
        dp[0] = true;
        for (int curr : nums) {
            for (int j = subSetSum; j >= curr; j--) {
                dp[j] |= dp[j - curr];
            }
        }
        return dp[subSetSum];
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}
```

## Output:
<img width="440" height="248" alt="image" src="https://github.com/user-attachments/assets/50817220-4953-4b4c-85de-965d8419e3d5" />

## Result:
The program successfully implemented and the expected output is verified.
