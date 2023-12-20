# Simple Array Sum

```java
   public static int simpleArraySum(List<Integer> ar) {
        return ar.stream().mapToInt(Integer::intValue).sum();
    }
```

# Plus Minus
```java
    public static void plusMinus(List<Integer> arr) {
        int len = arr.size();
        int positives = 0;
        int negatives = 0;
        int zeros = 0;

        // Counts the positives, negatives, and zeros
        for (int element : arr) {
            if (element > 0) {
                positives++;
            } else if (element < 0) {
                negatives++;
            } else {
                zeros++;
            }
        }
        // prints the ratios with 6 digits after the decimal
        System.out.printf("%.6f%n", (double) positives / len);
        System.out.printf("%.6f%n", (double) negatives / len);
        System.out.printf("%.6f%n", (double) zeros / len);
    }

```
# Staircase
```java
    public static void staircase(int n) {
        for (int i = 1; i <= n; i++) {
            StringBuilder stairBuilder = new StringBuilder();
            stairBuilder.append(" ".repeat(n - i));
            stairBuilder.append("#".repeat(i));
            System.out.println(stairBuilder.toString());
        }
    }   

```

# Mini-Max Sum
```java
    public static void miniMaxSum(List<Integer> arr) {
        
        List<Long> longarr = arr.stream().map(Integer::longValue).collect(Collectors.toList());
        Collections.sort(longarr);

        // sum without the last element (largest number)
        long mini = longarr.get(0) + longarr.get(1) + longarr.get(2) + longarr.get(3);
        
       // sum without the first element (smallest number)
        long max = longarr.get(1) + longarr.get(2) + longarr.get(3) + longarr.get(4);

        //Print the space-separated integers on one line
        System.out.println(mini + " " + max);

    }
```
# Diagonal difference
```java
    public static int diagonalDifference(List<List<Integer>> arr) {
        int sumFirst = 0;
        int sumSecond = 0;

        for (int i = 0; i < arr.size(); i++) {
            sumFirst += arr.get(i).get(i);
            sumSecond += arr.get(i).get(arr.size() - 1 - i);
        }

        //Absolute value of the difference
         return sumFirst > sumSecond ? sumFirst - sumSecond : sumSecond - sumFirst;
    }
```
# CamelCase
```java
    public static int camelcase(String s) {
        int count = 1;

        for (char c : s.toCharArray()) {
            if (Character.isUpperCase(c)) {
                count++;
            }
        }
        return count;

    }
```
# Weighted Uniform Strings
```java
    public static List<String> weightedUniformStrings(String s, List<Integer> queries) {
        Set<Integer> set = new HashSet<>();
    
        /* matches a letter and captures it as a group, then looks for occurrences
        of the captured letter repeating consecutively. */
        Matcher match = Pattern.compile("([a-z])\\1*").matcher(s);
        while(match.find()) {
            String uniform = match.group();
            int characterWeight = uniform.charAt(0) - 'a' + 1;
            //find out the weights of the found uniform string
            for(int multiplier = 1; multiplier <= uniform.length(); multiplier++) {
                int weight = multiplier * characterWeight;
                set.add(weight);
            }
    }
    
    //perform querying
    List<String> results = new ArrayList<>();
    for (int query : queries) {
        if(set.contains(query)) {
            results.add("Yes");
        }
        else results.add("No");
    }
    
    return results;
}
```
# Alternating Characters
```java
        public static int alternatingCharacters(String s) {
        if (s.length() <= 1) {
            return 0;
        }

        char firstChar = s.charAt(0);
        int i = 1;
        while (i < s.length() && s.charAt(i) == firstChar) {
            i++;
        }

        String remainder = s.substring(i);
        
        return (s.length() - remainder.length() - 1) + alternatingCharacters(remainder);
    }

```
# Insertion Sort Part I
```java
public static void insertionSort1(int n, List<Integer> arr) {
    int current = arr.get(n - 1);
    int i = n - 1;

    while (i > 0 && current < arr.get(i - 1)) {
        arr.set(i, arr.get(i - 1));
        i--;
        System.out.println(arr.stream().map(Object::toString).collect(Collectors.joining(" ")));
    }

    arr.set(i, current);
    System.out.println(arr.stream().map(Object::toString).collect(Collectors.joining(" ")));
}
```
# Insertion Sort Part II
```java
public static void insertionSort2(int n, List<Integer> arr) {
        for (int i = 1; i < n; i++) {
            int current = arr.get(i);
            int j = i - 1;
            while (j >= 0 && arr.get(j) > current) {
                arr.set(j + 1, arr.get(j));
                j--;
            }
            arr.set(j + 1, current);
            for (int k = 0; k < n; k++) {
                System.out.print(arr.get(k) + " ");
            }
            System.out.println();
        }
    }
```
# Runnint Time of Algorithms
```java
    public static int runningTime(List<Integer> arr) {
        int size = arr.size(); //size of array
        int s = 0;  // number of shifts

        for (int i = 1; i < size; i++) {
            int position = i - 1;
            int temp = arr.get(i);

            while (position >= 0 && arr.get(position) > temp) {
                arr.set(position + 1, arr.get(position));
                s++;
                position--;
            }
            arr.set(position + 1, temp);
        }
        return s;
    }
```
# Quicksort I: Partition
```java
    public static List<Integer> quickSort(List<Integer> arr) {
        if (arr.size() <= 1) {
            return arr;
        }

        List<Integer> left = new ArrayList<>();
        List<Integer> right = new ArrayList<>();

        for (int i = 1; i < arr.size(); i++) {
            if (arr.get(0) > arr.get(i)) {
                left.add(arr.get(i));
            } else {
                right.add(arr.get(i));
            }
        }

        List<Integer> result = new ArrayList<>();
        result.addAll(quickSort(left));
        result.add(arr.get(0));
        result.addAll(quickSort(right));

        return result;
    }
```
# Ice Cream Parlor
```java
    public static List<Integer> icecreamParlor(int m, List<Integer> arr) {
        Map<String, List<Integer>> memo = new HashMap<>();
        return getPrice(m, arr, 0, 1, memo);
    }

    public static List<Integer> getPrice(int m, List<Integer> arr, int index, int pointer, Map<String, List<Integer>> memo) {
        if (pointer == arr.size()) {
            return getPrice(m, arr, index + 1, index + 2, memo);
        } else if (pointer > arr.size()) {
            return new ArrayList<>();
        }

        String key = index + "-" + pointer;
        if (memo.containsKey(key)) {
            return memo.get(key);
        }

        List<Integer> result;
        if (arr.get(index) + arr.get(pointer) == m) {
            result = List.of(index + 1, pointer + 1);
        } else {
            result = getPrice(m, arr, index, pointer + 1, memo);
        }

        memo.put(key, result);
        return result;
    }
```
# Hackerland Radio Transmitters
```java
public static int hackerlandRadioTransmitters(List<Integer> x, int k) {
        Collections.sort(x);
        return hackerlandRadioTransmittersRecursive(x, k, 0, 0);
    }

    private static int hackerlandRadioTransmittersRecursive(List<Integer> x, int k, int currentPos, int count) {
        if (currentPos >= x.size()) {
            return count;
        }

        int possibleTowerPos = x.get(currentPos) + k;

        if (possibleTowerPos >= x.get(x.size() - 1)) {
            return count + 1;
        }

        int i;
        for (i = currentPos; i < x.size(); ++i) {
            if (x.get(i) >= possibleTowerPos) {
                break;
            }
        }

        if (x.get(i) != possibleTowerPos) {
            while (x.get(i) > possibleTowerPos) {
                i--;
            }
        }

        int rangeCovered = x.get(i) + k;

        int j;
        for (j = i; j < x.size(); ++j) {
            if (x.get(j) > rangeCovered) {
                break;
            }
        }

        return hackerlandRadioTransmittersRecursive(x, k, j, count + 1);
    }
```
# Fibonacci Modified
```java
     public static BigInteger fibonacciModified(int t1, int t2, int n) {
        List<BigInteger> memo = new ArrayList<>(n);
        memo.add(BigInteger.valueOf(t1));
        memo.add(BigInteger.valueOf(t2));
        
        for (int i = 2; i < n; i++) {
            BigInteger result = memo.get(i - 2).add(memo.get(i - 1).pow(2));
            memo.add(result);
        }
        
        return memo.get(n - 1);
    }
```
# Construct the Array
```java
    static long countArray(int n, int k, int x) {
        long a = 1, b = 0;

        for (int i = 0; i < n - 1; i++) {
            long ta = a, tb = b;
            a = ((1L * (k - 1) * tb) % 1000000007);
            b = (((1L * (k - 2) * tb) % 1000000007 + ta) % 1000000007);
        }

        return (x == 1) ? a : b;
    }
```
# Coin Change
```java
    public static long getWays(int n, List<Long> c) {
        List<Long> memo = new ArrayList<>(Collections.nCopies(n + 1, 0L));
        memo.set(0, 1L);

        for (long coin : c) {
            int coinValue = (int) coin; // Convert the long coin to an int once
            for (int amount = coinValue; amount <= n; amount++) {
                memo.set(amount, memo.get(amount) + memo.get(amount - coinValue));
            }
        }

        return memo.get(n);
    }
```
# Mars
```java
public static int marsExploration(String s) {
        String originalMessage = "SOS";
        int diff = 0;
        
        for(int i = 0; i < s.length()/3; i++) {
            String ss = s.substring(i*3,3*(1+i));
            if(!ss.equals(originalMessage)) {
                for(int j = 0; j < 3; j++) {
                    if(originalMessage.charAt(j) != ss.charAt(j)) {
                        diff++;
                    }
                }
                    
            }
                
        }
        return diff;
    }
```
# Hacker Rank in a String
```java


```
# Correctness and the Loop Invariant
```java


```
# Two strings
```java


```
