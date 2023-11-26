```java
import java.util.Scanner;

public class Main {
    // 找到最长连续上涨天数的函数
    static int find(int n, int[] prices) {
        if (n <= 0) {
            return 0;
        }

        int maxLength = 1;      // 最长连续上涨天数
        int currentLength = 1;  // 当前连续上涨天数

        for (int i = 1; i < n; ++i) {
            if (prices[i] > prices[i - 1]) {
                // 如果第i天的价格比第i-1天的价格高，连续上涨天数加一
                currentLength++;
            } else {
                // 当前价格不高于前一天，重置连续上涨天数
                currentLength = 1;
            }

            // 更新最大连续上涨天数
            maxLength = Math.max(maxLength, currentLength);
        }

        return maxLength;  // 返回最长连续上涨天数
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] prices = new int[n];  // 用来存储股票的价格的数组
        for (int i = 0; i < n; ++i) {
            // 输入股票的价格
            prices[i] = scanner.nextInt();
        }

        int result = find(n, prices);  // 找到最长连续上涨天数
        System.out.println(result);     // 输出最长连续上涨天数
    }
}

```