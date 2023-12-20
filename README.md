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
