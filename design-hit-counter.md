# Design Hit Counter
Java approach (linear getHits() time complexity):
```
public class HitCounter {

    //count hit in the past 5 minutes = 300s

    Queue<Integer> hits;

    /** Initialize your data structure here. */
    public HitCounter() {
        this.hits = new LinkedList<>();
    }

    /** Record a hit.
     @param timestamp - The current timestamp (in seconds granularity). */
    public void hit(int timestamp) {
        this.hits.offer(timestamp);
        while(timestamp - this.hits.peek() > 300){
            int temp = this.hits.remove(); //remove first timestamp
            System.out.println("Removed " + temp);
        }
    }

    /** Return the number of hits in the past 5 minutes.
     @param timestamp - The current timestamp (in seconds granularity). */
    public int getHits(int timestamp) {
        //count hits
        int result = 0;
        for(Integer i : this.hits){
            if(i <= timestamp && timestamp - i < 300){
                ++ result;
            }
        }
        return result;
    }

    public static void main(String[] args){
        HitCounter counter = new HitCounter();
        counter.hit(1);
        counter.hit(2);
        counter.hit(3);
        System.out.println(counter.getHits(4));
        counter.hit(300);
        System.out.println(counter.getHits(300));
        System.out.println(counter.getHits(301));
    }
}

```