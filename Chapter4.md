# 第四章

1.代码如下：
```c
#include <stdio.h>

int gcd(int a, int b) {
    int temp;
    while (b > 0) {
        temp = a % b;
        a = b;
        b = temp;
    }
    return a;
}

int main() {
    int a, b;
    scanf("%d %d", &a, &b);
    int g = gcd(a, b);
    printf("%d %d", g, a*b/g);
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>
#include <string.h>

int main() {
    char line[1000];
    // 读一行
    scanf("%[^\n]",&line);
    int digit_count = 0, alpha_count = 0, space_count = 0, other_count = 0, len = strlen(line);
    for (int i = 0; i < len; i++) {
        if (line[i] == ' ') {
            space_count++;
        } else if (line[i] >= '0' && line[i] <= '9') {
            digit_count++;
        } else if ((line[i] >= 'a' && line[i] <= 'z') || (line[i] >= 'A' && line[i] <= 'Z')) {
            alpha_count++;
        } else {
            other_count++;
        }
    }
    printf("%d %d %d %d", alpha_count, digit_count, space_count, other_count);
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    int base = 2, temp = 0, sum = 0;
    for (int i = 0; i < n; i++) {
        temp *= 10;
        temp += base;
        sum += temp;
    }
    printf("%d", sum);
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    long sum = 0, temp = 1;
    for (int i = 1; i <= n; i++) {
        temp *= i;
        sum += temp;
    }
    printf("%ld", sum);
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    double sum = 0, i;
    for (i = 1; i <= a; i++) {
        sum += i;
    }
    for (i = 1; i <= b; i++) {
        sum += i*i;
    }
    for (i = 1; i <= c; i++) {
        sum += 1.0/i;
    }
    printf("%.2lf", sum);
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b, c;
    for (int i = 100; i <= 999; i++) {
        c = i;
        a = c/100;
        c %= 100;
        b = c / 10;
        c %= 10;
        if (a*a*a + b*b*b + c*c*c == i) {
            printf("%d\n", i);
        }
    }
    return 0;
}
```

7.代码如下：
```c
#include <stdio.h>

int main() {
    int sum, n, ptr, i, j;
    scanf("%d", &n);
    int arr[n];
    for (i = 1; i < n; i++) {
        sum = 0;
        ptr = 0;
        for (j = 1; j < i; j++) {
            if (i % j == 0) {
                arr[ptr] = j;
                ptr++;
                sum += j;
            }
        }
        if (i == sum) {
            printf("%d its factors are", i);
            for (j = 0; j < ptr; j++) {
                printf(" %d", arr[j]);
            }
            printf("\n");
        }
    }
    return 0;
}
```

8.代码如下：
```c
#include <stdio.h>

int main() {
    int a = 1, b = 2, n, temp;
    scanf("%d", &n);
    double sum = 0;
    for (int i = 0; i <n; i++) {
        sum += (double)b/a;
        temp = b;
        b += a;
        a = temp;
    }
    printf("%.2lf", sum);
    return 0;
}
```

9.代码如下：
```c
#include <stdio.h>

int main() {
    double m;
    int n;
    scanf("%lf %d", &m, &n);
    double sum = 0, temp = m;
    for (int i = 0; i < n; i++) {
        sum += temp;
        temp /= 2;
        sum += temp;
    }
    sum -= temp;
    printf("%.2lf %.2lf", temp, sum);
    return 0;
}
```

10.代码如下：
```c
#include <stdio.h>

int main() {
    int day, sum = 1;
    scanf("%d", &day);
    for (int i = 1; i < day; i++) {
        sum += 1;
        sum *= 2;
    }
    printf("%d", sum);
    return 0;
}
```

11.代码如下：
```c
#include <stdio.h>

int main() {
    double n;
    scanf("%lf", &n);
    double prev = 0, temp = 1;
    while (temp - prev >= 0.00001 || temp - prev <= -0.00001) {
        prev = temp;
        temp = (prev + n/prev) / 2;
    }
    printf("%.3lf", temp);
    return 0;
}
```

- [下一章](/Chapter5.md)
- [返回目录](/README.md)
