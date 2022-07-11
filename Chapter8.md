# 第八章

1.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    if (a > b && b > c) {
        printf("%d %d %d", c, b, a);
    } else if (a > c && c > b) {
        printf("%d %d %d", b, c, a);
    } else if (b > a && a > c) {
        printf("%d %d %d", c, a, b);
    } else if (b > c && c > a) {
        printf("%d %d %d", a, c, b);
    } else if (c > a && a > b) {
        printf("%d %d %d", b, a, c);
    } else {
        printf("%d %d %d", a, b, c);
    }
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[100], str2[100], str3[100];
    scanf("%s %s %s", str1, str2, str3);
    if (strcmp(str1, str2) > 0 && strcmp(str2, str3) > 0) {
        printf("%s\n%s\n%s", str3, str2, str1);
    } else if (strcmp(str1, str3) > 0 && strcmp(str3, str2) > 0) {
        printf("%s\n%s\n%s", str2, str3, str1);
    } else if (strcmp(str2, str1) > 0 && strcmp(str1, str3) > 0) {
        printf("%s\n%s\n%s", str3, str1, str2);
    } else if (strcmp(str2, str3) > 0 && strcmp(str3, str1) > 0) {
        printf("%s\n%s\n%s", str1, str3, str2);
    } else if (strcmp(str3, str1) > 0 && strcmp(str1, str2) > 0) {
        printf("%s\n%s\n%s", str2, str1, str3);
    } else {
        printf("%s\n%s\n%s", str1, str2, str3);
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

int main() {
    int n = 10, arr[n];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    int min_index = 0, max_index = 0;
    for (int i = 0; i < n; i++) {
        if (arr[i] > arr[max_index]) {
            max_index = i;
        }
        if (arr[i] < arr[min_index]) {
            min_index = i;
        }
    }
    int temp = arr[max_index];
    arr[max_index] = arr[n-1];
    arr[n-1] = temp;
    temp = arr[min_index];
    arr[min_index] = arr[0];
    arr[0] = temp;
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>

int main() {
    int n, m;
    scanf("%d", &n);
    int nums[n];
    for (int i = 0; i < n; i++) {
        scanf("%d", &nums[i]);
    }
    scanf("%d", &m);
    for (int i = n-m; i < n; i++) {
        printf("%d ", nums[i]);
    }
    for (int i = 0; i < n-m; i++) {
        printf("%d ", nums[i]);
    }
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>
#include <stdlib.h>

typedef struct people People;

struct people {
    int id;
    struct people *next;
};

int main() {
    int n, ptr = 0;
    scanf("%d", &n);
    People *head = malloc(sizeof(People)), *p = head;
    head->id = 1;
    head->next = head;
    for (int i = 2; i <= n; i++) {
        People *newPeople = malloc(sizeof(People));
        newPeople->id = i;
        p->next = newPeople;
        newPeople->next = head;
        p = newPeople;
    }
    p = head;
    while (p->next != p) {
        p = p->next;
        p->next = p->next->next;
        p = p->next;
    }
    printf("%d", p->id);
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>

int main() {
    int len, from;
    char str[100];
    scanf("%d", &len);
    scanf("%s", str);
    scanf("%d", &from);
    for (int i = from-1; i < len; i++) {
        printf("%c", str[i]);
    }
    return 0;
}
```

- [下一章](/Chapter9.md)
- [返回目录](/README.md)
