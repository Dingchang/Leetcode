# 367. Valid Perfect Square

```
public boolean isPerfectSquare(int num) {
    if (num == 1) {
        return true;
    }

    int low = 1;
    int high = num - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if ((double)num / (double)mid == (double)mid) {
            return true;
        } else if (num / mid > mid) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    return false;
}
```
