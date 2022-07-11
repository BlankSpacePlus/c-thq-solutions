# 第三章

1.代码如下：
```c
#include <stdio.h>

int main() {
    double f;
    scanf("%lf", &f);
    printf("c=%.2lf", 5*(f-32)/9);
    return 0;
}
```

2.代码如下(这题只需要输入整数即可)：
```c
#include <stdio.h>

int main() {
    int x;
    scanf("%d", &x);
    if (x < 1) {
        printf("%d", x);
    } else if (x < 10) {
        printf("%d", 2*x-1);
    } else {
        printf("%d", 3*x-11);
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

int main() {
    int grade;
    scanf("%d", &grade);
    if (grade < 60) {
        printf("E");
    } else if (grade < 70) {
        printf("D");
    } else if (grade < 80) {
        printf("C");
    } else if (grade < 90) {
        printf("B");
    } else {
        printf("A");
    }
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>
#include <string.h>

int main() {
    char num[10];
    scanf("%s", num);
    int len = strlen(num);
    printf("%d\n", len);
    for (int i = 0; i < len; i++) {
        printf("%c ", num[i]);
    }
    printf("\n");
    for (int i = len-1; i >= 0; i--) {
        printf("%c", num[i]);
    }
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>
#include <string.h>

int main() {
    int salary;
    scanf("%d", &salary);
    double sum = 0.0;
    if (salary > 1000000) {
        sum += (salary-1000000)*0.01;
        salary = 1000000;
    }
    if (salary > 600000) {
        sum += (salary-600000)*0.015;
        salary = 600000;
    }
    if (salary > 400000) {
        sum += (salary-400000)*0.03;
        salary = 400000;
    }
    if (salary > 200000) {
        sum += (salary-200000)*0.05;
        salary = 200000;
    }
    if (salary > 100000) {
        sum += (salary-100000)*0.075;
        salary = 100000;
    }
    sum += salary*0.1;
    printf("%d", (int)sum);
    return 0;
}
```

- [下一章](/Chapter4.md)
- [返回目录](/README.md)
