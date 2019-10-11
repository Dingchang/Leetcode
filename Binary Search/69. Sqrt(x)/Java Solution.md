# 69. Sqrt(x)

```
public int mySqrt(int x) {
    if (x == 0 || x == 1) {
        return x;
    }

    int low = 1;
    int high = x - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (x / mid == mid) {
            return mid;
        } else if (x / mid > mid) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    return low - 1;
}
```
