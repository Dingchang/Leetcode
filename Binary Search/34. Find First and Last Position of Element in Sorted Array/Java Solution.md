# First and Last Position of Element in Sorted Array

## Binary Search
```
private int binarySearch(int[] nums, int target, boolean findLeftmost) {   
    int low = 0;
    int high = nums.length;

    if (findLeftmost) {
        while (low < high) {
            int mid = (low + high) / 2;
            if (nums[mid] >= target) {
                high = mid;
            } else {
                low = mid + 1;
            }
        }

        return low;
    } else {
        while (low < high) {
            int mid = (low + high) / 2;
            if (nums[mid] > target) {
                high = mid;
            } else {
                low = mid + 1;
            }
        }

        return low;
    }
}

public int[] searchRange(int[] nums, int target) {
    int[] result = { -1, -1 };
    int left = binarySearch(nums, target, true);

    if (left == nums.length || nums[left] != target) {
        return result;
    }

    result[0] = left;
    result[1] = binarySearch(nums, target, false) - 1;

    return result;
}
```
