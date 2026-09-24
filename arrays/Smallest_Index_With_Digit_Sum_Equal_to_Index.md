```c
//This is leetcode problem 3550. Smallest Index With Digit Sum Equal to Index: https://leetcode.com/problems/smallest-index-with-digit-sum-equal-to-index/?envType=daily-question&envId=2026-09-24
int smallestIndex(int* nums, int numsSize) {
    for(int i = 0; i < numsSize; i++){
        if(nums[i] >= 1000){ //one of the constraints was the value of nums[i] <= 1000, so we only have to check cases up to four digits.
            int thousands = nums[i]/1000; //essentially all these int values end up in singular digits of the number.
            int hundreds = nums[i]/10 % 10;
            int tens = nums[i]/100 % 10;
            int ones = nums[i]%10;
            if((thousands + hundreds + tens + ones) == i){
                return i;
            }
        }
        if(nums[i] >= 100){
            int hundreds = nums[i] / 100; //since int doesn't store decimal numbers, when something like 325 is divded by 100, it results in just 3.
            int tens = nums[i]/10 % 10; //for this, if we had 345 this time, dividing by 10 would result in 34, then taking the remainder would give 4.
            int ones = nums[i] % 10; //just taking the remainder when dividing by 10 results in the ones digit. 
            if((hundreds + tens + ones) == i){ 
                return i;
            }
        }
        if(nums[i] >= 10){
            int tens = nums[i]/10;
            int ones = nums[i]%10;
            if((tens + ones) == i){
                return i;
            }
        }
        if(nums[i] >= 0){
            int ones = nums[i];
            if(ones == i){
                return i;
            }
        }
    }
    return -1; 
}
```
