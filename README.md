# Leetcode---2099
Find Subsequence of Length K With the Largest
//code in java 
import java.util.*;

class Solution {
    public int[] maxSubsequence(int[] nums, int k) {
        int n = nums.length;
        
        // Create an array of pairs: (value, index)
        int[][] pairs = new int[n][2];
        for (int i = 0; i < n; i++) {
            pairs[i][0] = nums[i];
            pairs[i][1] = i;
        }
        
        // Sort based on values in descending order
        Arrays.sort(pairs, (a, b) -> b[0] - a[0]);
        
        // Get top k elements
        Arrays.sort(pairs, 0, k, Comparator.comparingInt(a -> a[1]));

        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = pairs[i][0];
        }
        return result;
    }
}
