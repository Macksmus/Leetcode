/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
//this is first leetcode problem, TwoSum https://leetcode.com/problems/two-sum/
#include <stdlib.h>
int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    for(int i = 0; i < numsSize; i++){
        for(int j = i+1; j < numsSize; j++){ //starting j at i+1 ensures that the if statement doesn't look for the same index twice, and it's okay in this case because if i = 2, j doesn't have to go back to nums[1] because there's already been a case of i = 1 and j = 2. 
            if(nums[i] + nums[j] == target){
                int* result = (int*)(malloc(2 * sizeof(int))); 
                result[0] = i;
                result[1] = j;
                *returnSize = 2; 
                return result; 
            }
        }
    }
    return 0;
}
