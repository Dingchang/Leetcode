# 33. Search in Rotated Sorted Array

```
public int search(int[] nums, int target) {
    int low = 0;
    int high = nums.length - 1;

    while(low <= high) {
        int mid = (low + high) / 2;
        if(nums[low] == target) {
            return low;
        } else if(nums[mid] == target) {
            return mid;
        } else if(nums[high] == target) {
            return high;
        } else if(nums[low] > target) {
            if( nums[mid] > target && nums[mid] < nums[low]) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }              
        } else if(nums[low] < target){
            if(nums[mid] < target && nums[mid] > nums[low]) {
                low = mid + 1;
            } else  {
                high = mid - 1;
            }           
        }
    }

    return -1;
}
```
