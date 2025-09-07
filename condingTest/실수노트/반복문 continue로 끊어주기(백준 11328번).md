반복문 continue로 끊어주기(백준 11328번)
==

당연하고 당연한거지만
푼 문제 중에 continue를 쓰는 상황이 그렇게 많지는 않은데 그렇다 보니 한번씩 까먹고 넘어갈 수 있다 싶어서 쓰는 중

아래 코드에서 두 문자열의 길이가 다르면 Impossible을 출력하고 그 다음 전체 루프를 돌도록 할 예정이었다. 근데 처음에 continue를 안써서 뭘까 한참 생각했다.

따라서 출력 후 다음 전체 루프로 넘겨주기 위해 Continue 쓰는 것을 잊지 말자!!

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        for (int i = 0; i < n; i++) {
            String str = sc.next();
            String str1 = sc.next();

            if (str.length() != str1.length()) {
                System.out.println("Impossible");
                continue;
            }

            int[] arr = new int[26];
            for (int j = 0; j < str.length(); j++) {
                arr[str.charAt(j) - 'a']++;
                arr[str1.charAt(j) - 'a']--;
            }

            boolean possible = true;
            for (int num : arr) {
                if (num != 0) {
                    possible = false;
                    break;
                }
            }

            if (possible) {
                System.out.println("Possible");
            } else {
                System.out.println("Impossible");
            }
        }
    }
}

```