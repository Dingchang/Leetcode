# 981. Time Based Key-Value Store

## HashMap + Binary Search
```
import javafx.util.Pair;

class TimeMap {
    Map<String, List<Pair<Integer, String>>> map;

    public TimeMap() {
        this.map = new HashMap();
    }

    public void set(String key, String value, int timestamp) {
        if (!map.containsKey(key)) {
            map.put(key, new ArrayList<Pair<Integer, String>>());
        }

        map.get(key).add(new Pair(timestamp, value));
    }

    public String get(String key, int timestamp) {
        if (!map.containsKey(key)) {
            return "";
        }

        List<Pair<Integer, String>> list = map.get(key);
        int low  = 0;
        int high = list.size() - 1;

        while (low <= high) {
            int mid = (high + low) / 2;
            int ts  = list.get(mid).getKey();
            String value = list.get(mid).getValue();

            if (ts == timestamp) {
                return value;
            } else if (ts > timestamp) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }

        if (high >= 0) {
            return list.get(high).getValue();
        } else {
            return "";
        }
    }
}
```
