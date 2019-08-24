# Two Sum

## Brute Force
```
int* twoSum(int* nums, int numsSize, int target, int* returnSize){
  int* result = (int*) malloc(2 * sizeof(int));
  *returnSize = 2;
  for (int i = 0; i < numsSize; i++){
    for (int j = i + 1; j < numsSize; j++){
      if (nums[i] + nums[j] == target){
        result[0] = i;
        result[1] = j;
      }
    }  
  }
  return result;
}
```

## One-pass Hash Table
```
#define SIZE 50000

int hash(int key) {
  int r = key % SIZE;
  return r < 0 ? r + SIZE : r;
}

void insert(int* keys, int* values, int key, int value) {
  int index = hash(key);
  while (values[index]) {
    index = (index + 1) % SIZE;
  }
  keys[index] = key;
  values[index] = value;
}

int search(int* keys, int* values, int key) {
  int index = hash(key);
  while (values[index]) {
    if (keys[index] == key) {
      return values[index];
    }
    index = (index + 1) % SIZE;
  }
  return 0;
}

int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
  int keys[SIZE];
  int values[SIZE] = {0};
  *returnSize = 2;
  for (int i = 0; i < numsSize; i++) {
    int complements = target - nums[i];
    int value = search(keys, values, complements);
    if (value) {
      int* result = (int*) malloc(sizeof(int) * 2);
      result[0] = value - 1;
      result[1] = i;
      return result;
    }
    insert(keys, values, nums[i], i + 1);
  }
  return NULL;
}
```
