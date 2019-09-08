# 704. Binary Search

## Binary search
```
int search(int* nums, int numsSize, int target) {
    int low = 0;
    int high = numsSize;

    while (low < high) {
        int mid = (low + high) / 2;
        if (nums[mid] >= target) {
            high = mid;
        } else {
            low = mid + 1;
        }
    }

    return (low == numsSize || nums[low] != target) ? -1 : low;
}
```

## Alternative solution
```
int search(int* nums, int numsSize, int target) {
    int low = 0;
    int high = numsSize - 1;

    while (low <= high) {
        int mid = (low + high) / 2;

        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] > target) {
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }

    return -1;
}
```
