배열 index 검증(백준 3273번)
==

런타임 에러 발생!!! -> 보통 배열을 쓸 때 런타임 에러가 발생하면 배열 index 문제일 확률이 높다.
예전에도 계속 했던 실수!

아래 코드를 보자

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] numArr = new int[n];
        int[] arr = new int[1000001];
        int result = 0;

        for (int i = 0; i < n; i++) {
            int num = sc.nextInt();
            numArr[i] = num;
            arr[num]++;
        }
        int x = sc.nextInt();

        for (int i : numArr) {
            if (arr[x-i] == 1) result++;
        }

        System.out.println(result / 2);
    }
}
```

아래의 이 부분에서

if (arr[x-i] == 1) result++;

x가 i보다 작다면 문제가 발생한다.

따라서 x

```java
for (int i : numArr) {
            int target = x - i;
            if (target >= 1 && target <= 1000000) {
                if (arr[target] == 1) result++;
            }
        }
```

이런식으로 index 값을 검증하는게 필요!! 까먹지 말자