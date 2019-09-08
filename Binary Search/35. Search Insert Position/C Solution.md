# Search Inseart Position

## Variation 1
```
int searchInsert(int* nums, int numsSize, int target){
  int low = 0;
  int high = numsSize;

  while (low < high) {
    int mid = (low + high) / 2;
    if (target > nums[mid]) {
      low = mid + 1;
    } else {
      high = mid;
    }
  }

  return low;
}
```

## Variation 2
```
int searchInsert(int* nums, int numsSize, int target){
  int low = 0;
  int high = numsSize - 1;

  while (low <= high) {
    int mid = (low + high) / 2;
    if (target > nums[mid]) {
      low = mid + 1;
    } else {
      high = mid - 1;
    }
  }

  return low;
}
```
