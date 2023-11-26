```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String[] name = new String[10005];
        int[] height = new int[10005];

        int n = scanner.nextInt();
        for (int i = 0; i < n; i++) {
            name[i] = scanner.next();
            height[i] = scanner.nextInt();
        }

        // 根据身高排序
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n - 1 - i; j++) {
                if (height[j] > height[j + 1]) {
                    // Swap height
                    int temp = height[j];
                    height[j] = height[j + 1];
                    height[j + 1] = temp;

                    // Swap name
                    String temp1 = name[j];
                    name[j] = name[j + 1];
                    name[j + 1] = temp1;
                }
            }
        }

        for (int i = 0; i < n; i++) {
            System.out.println(name[i] + " " + height[i]);
        }
    }
}

```
