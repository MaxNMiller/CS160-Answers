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


```
# Diagonal difference
```java


```
# CamelCase
```java


```
# Weighted Uniform Strings
```java


```
# Alternating Characters
```java


```
# Insertion Sort Part I
```java


```
# Insertion Sort Part II
```java


```
# Runnint Time of Algorithms
```java


```
# Ice Cream Parlor
```java


```
# Fibonacci Modified
```java


```
# Construct the Array
```java


```
# Coin Change
```java


```
# Mars
```java


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
