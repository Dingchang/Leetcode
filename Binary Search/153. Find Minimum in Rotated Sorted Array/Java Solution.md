# 153. Find Minimum in Rotated Sorted Array

```
public int findMin(int[] nums) {
    int low = 0;
    int high = nums.length - 1;

    while (low < high) {
        int mid = low + (high - low) / 2;

        if (nums[mid] < nums[mid + 1]) {
            if (nums[mid] > nums[high]) {
                low = mid + 1;
            } else {
                high = mid;
            }
        } else {
            return nums[mid + 1];
        }
    }

    return nums[low];
}
```
