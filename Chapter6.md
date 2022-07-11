# 第六章

1.代码如下：
```c
#include <stdio.h>

int gcd1(int a, int b) {
    int temp;
    while (b > 0) {
        temp = a % b;
        a = b;
        b = temp;
    }
    return a;
}

int gcd2(int a, int b) {
    return a*b/gcd1(a,b);
}

int main() {
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d %d", gcd1(a, b), gcd2(a, b));
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>
#include <math.h>

void f1(int a, int b, int c) {
    double x1 = (-b + sqrt(b*b-4*a*c)) / (2*a), x2 = (-b - sqrt(b*b-4*a*c)) / (2*a);
    printf("x1=%.3lf x2=%.3lf", x1, x2);
}

void f2(int a, int b, int c) {
    double x = -(double)b/(2*a);
    printf("x1=%.3lf x2=%.3lf", x, x);
}

void f3(int a, int b, int c) {
    double x = -(double)b/(2*a);
    double y = sqrt(4*a*c-b*b) / (2*a);
    printf("x1=%.3lf+%.3lfi x2=%.3lf-%.3lfi", x, y, x, y);
}

int main() {
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    double delta = b*b-4*a*c;
    if (delta > 0) {
        f1(a, b, c);
    } else if (delta == 0) {
        f2(a, b, c);
    } else {
        f3(a, b, c);
    }
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>

int isPrime(int x) {
    for (int i = 2; i < x; i++) {
        if (x % i == 0) {
            return 0;
        }
    }
    return 1;
}

int main() {
    int x;
    scanf("%d", &x);
    printf("%sprime", isPrime(x) ? "" : "not ");
    return 0;
}
```

4.代码如下（犯过一个错误是扫了整个矩阵所以交换了两次等于没换）：
```c
#include <stdio.h>

void reverse(int *matrix, int n) {
    int temp;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < i; j++) {
            temp = *(matrix+n*i+j);
            *(matrix+n*i+j) = *(matrix+n*j+i);
            *(matrix+n*j+i) = temp;
        }
    }
}

int main() {
    int n = 3, matrix[n][n];
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
    reverse((int *) matrix, n);
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>

int get_len(char *line) {
    char temp = *line;
    int counter = 1;
    while (temp != '\0') {
        temp = *(line+counter);
        counter++;
    }
    return --counter;
}

void reverse(char *line) {
    int len = get_len(line), temp;
    for (int i = 0; i < len/2; i++) {
        temp = *(line+len-1-i);
        *(line+len-1-i) = *(line+i);
        *(line+i) = temp;
    }
}

int main() {
    char line[1000];
    scanf("%s", line);
    reverse((char *)line);
    printf("%s", line);
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>
#include <stdlib.h>

int get_len(char *line) {
    char temp = *line;
    int counter = 1;
    while (temp != '\0') {
        temp = *(line+counter);
        counter++;
    }
    return --counter;
}

char *str_cat(char *str1, char *str2) {
    int len1 = get_len(str1), len2 = get_len(str2);
    char *p = malloc(len1+len2);
    for (int i = 0; i < len1; i++) {
        *(p+i) = *(str1+i);
    }
    for (int i = 0; i < len2; i++) {
        *(p+len1+i) = *(str2+i);
    }
//    free(str1);
//    free(str2);
    return p;
}

int main() {
    char line1[1000], line2[1000], *p;
    scanf("%s %s", line1, line2);
    p = str_cat(line1, line2);
    printf("%s", p);
//    free(p);
    return 0;
}
```

7.代码如下：
```c
#include <stdio.h>
#include <stdlib.h>

int get_len(char *line) {
    char temp = *line;
    int counter = 1;
    while (temp != '\0') {
        temp = *(line+counter);
        counter++;
    }
    return --counter;
}

char *get_vowel(char *str1) {
    int len1 = get_len(str1), ptr = 0;
    char *arr = malloc(len1);
    for (int i = 0; i < len1; i++) {
        if (str1[i] == 'a' || str1[i] == 'e' || str1[i] == 'i' || str1[i] == 'o' || str1[i] == 'u') {
            arr[ptr] = str1[i];
            ptr++;
        }
    }
    arr[ptr] = '\0';
    return arr;
}

int main() {
    char line[1000], *p;
    scanf("%s", line);
    p = get_vowel(line);
    printf("%s", p);
    return 0;
}
```

8.代码如下：
```c
#include <stdio.h>

void getNumBits(int num) {
    int temp, now = 1, i = 0, nums[100];
    while (num > 0) {
        temp = num % (now*10);
        temp /= now;
        num -= temp*now;
        now *= 10;
        nums[i++] = temp;
    }
    for (int j = i-1; j >= 0; j--) {
        printf("%d ", nums[j]);
    }
}

int main() {
    int num;
    scanf("%d", &num);
    getNumBits(num);
    return 0;
}
```

9.代码如下：
```c
#include <stdio.h>
#include <string.h>

void char_count(char *line, int *alpha, int *digit, int *space, int *other) {
    int len = strlen(line);
    for (int i = 0; i < len; i++) {
        if (line[i] == ' ') {
            (*space)++;
        } else if (line[i] >= '0' && line[i] <= '9') {
            (*digit)++;
        } else if ((line[i] >= 'a' && line[i] <= 'z') || (line[i] >= 'A' && line[i] <= 'Z')) {
            (*alpha)++;
        } else {
            (*other)++;
        }
    }
}

int main() {
    char line[1000];
    // 读一行
    scanf("%[^\n]", line);
    int digit_count = 0, alpha_count = 0, space_count = 0, other_count = 0;
    int *alpha = &alpha_count, *digit = &digit_count, *space = &space_count, *other = &other_count;
    char_count(line, alpha, digit, space, other);
    printf("%d %d %d %d", alpha_count, digit_count, space_count, other_count);
    return 0;
}
```

- [下一章](/Chapter7.md)
- [返回目录](/README.md)
