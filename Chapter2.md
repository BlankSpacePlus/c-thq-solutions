# 第二章

1.代码如下：
```c
#include <stdio.h>

int main() {
    float r, h, PI = 3.14;
    scanf("%f %f", &r, &h);
    printf("C1=%.2f\nSa=%.2f\nSb=%.2f\nVa=%.2f\nVb=%.2f", 2*PI*r, PI*r*r, 4*PI*r*r, 4*PI*r*r*r/3, PI*r*r*h);
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

int main() {
    double f;
    scanf("%lf", &f);
    printf("c=%.2lf", 5*(f-32)/9);
    return 0;
}
```

- [下一章](/Chapter3.md)
- [返回目录](/README.md)
