# 第五章

1.代码如下：
```c
#include <stdio.h>

int main() {
    int n, flag = 1;
    scanf("%d", &n);
    for (int i = 2; i <= n; i++) {
        flag = 1;
        for (int j = 2; j < i; j++) {
            if (i % j == 0) {
                flag = 0;
                break;
            }
        }
        if (flag) {
            printf("%d\n", i);
        }
    }
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

int main() {
    int n = 10, arr[10], min_index, temp;
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    for (int i = 0; i < n-1; i++) {
        min_index = i;
        for (int j = i+1; j < n; j++) {
            if (arr[j] < arr[min_index]) {
                min_index = j;
            }
        }
        temp = arr[i];
        arr[i] = arr[min_index];
        arr[min_index] = temp;
    }
    for (int i = 0; i < n; i++) {
        printf("%d\n", arr[i]);
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

int main() {
    int n = 3, matrix[n][n], sum = 0;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
    for (int i = 0; i < n; i++) {
        sum += matrix[i][i];
    }
    printf("%d ", sum);
    sum = 0;
    for (int i = 0; i < n; i++) {
        sum += matrix[i][2-i];
    }
    printf("%d", sum);
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>

int main() {
    int n = 9, arr[n], num, flag = 0;
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    scanf("%d", &num);
    for (int i = 0; i < n; i++) {
        if (flag || arr[i] < num) {
            printf("%d ", arr[i]);
        } else {
            flag = 1;
            printf("%d %d ", num, arr[i]);
        }
    }
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>

int main() {
    int n = 10, arr[n];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    for (int i = n-1; i >= 0; i--) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```

- [下一章](/Chapter6.md)
- [返回目录](/README.md)
