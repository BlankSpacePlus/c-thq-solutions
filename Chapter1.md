# 第一章

1.代码如下：
```c
#include <stdio.h>

int main() {
    printf("**************************\n         Very    Good!\n**************************\n");
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

int main() {
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    printf("%d", (a>b&&a>c) ? a : (b>a&&b>c) ? b : c);
    return 0;
}
```

- [下一章](/Chapter2.md)
- [返回目录](/README.md)
