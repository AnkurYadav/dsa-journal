# LC 853 - car-fleet

**Difficulty:** Medium
**Pattern:** monotonic stack
**Link:** https://leetcode.com/problems/car-fleet

## Approach

sort the cars based on their distance to target, now iterate over the cars list and check if the fleet in front has time to target lesser or greater, if lesser then a new fleet will be created with current car if greater then current car will merge with the last fleet, then in the end total no. of fleets would be there

## Code

```java
class Car {
    public int distanceToTarget;
    public double time;

    public Car(int position, int speed, int target) {
        this.distanceToTarget = target - position;
        this.time = ((double)distanceToTarget)/speed;
    }
}

class Solution {
    public int carFleet(int target, int[] position, int[] speed) {
        Car[] cars = new Car[position.length];
        for(int i = 0; i < cars.length; i++) {
            cars[i] = new Car(position[i], speed[i], target);
        }

        Arrays.sort(cars, Comparator.comparingInt(c -> c.distanceToTarget));

        int fleetCount = 0;
        double lastFleetTime = 0;
        for(int i = 0; i < cars.length; i++) {
            if(lastFleetTime < cars[i].time) {
                fleetCount++;
                lastFleetTime = cars[i].time;
            }
        }

        return fleetCount;
    }
}
```

## Complexity

- Time: O(nlog(n) + n)
- Space: O(n)

## Gotcha

only needs to check the last fleet since car would merge with next fleet just in front only
