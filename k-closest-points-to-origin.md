# K Closest Points to Origin
Draft Java solution:
```
    public int[][] kClosest(int[][] points, int K) {
        //TreeSet + precedence approach
        int[][] result = new int[K][2];
        int[][] temp = new int[points.length][3];
        if(points.length == 0){
            return result;
        }
        Set<int[]> set = new TreeSet<>(new Comparator<int[]>(){
            @Override
            public int compare(int[] a, int[] b){
                double diff = (Math.pow(a[0], 2) + Math.pow(a[1], 2)) - (Math.pow(b[0], 2) + Math.pow(b[1], 2));
                if(diff == 0.0){
                    return a[2] - b[2];
                }
                return diff > 0 ? 1 : -1;
            }
        });

        for(int i = 0; i < points.length; ++ i){
            temp[i][0] = points[i][0];
            temp[i][1] = points[i][1];
            temp[i][2] = i; //assign precedence
        }

        for(int[] point : temp){
            set.add(point);
        }
        for(int i = 0; i < K; ++ i){
            int[] closePoint = ((TreeSet<int[]>) set).pollFirst();
            result[i][0] = closePoint[0];
            result[i][1] = closePoint[1];
        }
        return result;
    }
```
PASSED with 6 attempts. 