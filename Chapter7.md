# 第七章

1.代码如下：
```c
#include <stdio.h>

#define SWAP(a,b) t=a; a=b; b=t;

int main() {
    int x,y,t;
    scanf("%d %d", &x, &y);
    SWAP(x,y);
    printf("%d %d", x, y);
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

#define MOD(a,b) t=a%b;

int main() {
    int x, y, t;
    scanf("%d %d", &x, &y);
    MOD(x, y);
    printf("%d", t);
    return 0;
}
```

3.代码如下：
```c
#include <stdio.h>
#include <math.h>

#define GETS(a,b,c) s=((double)a+b+c)/2;

#define AREA(a,b,c,s) area=sqrt(s*(s-a)*(s-b)*(s-c));

int main() {
    int a, b, c;
    double s, area;
    scanf("%d %d %d", &a, &b, &c);
    GETS(a, b, c);
    AREA(a, b, c, s);
    printf("%.3lf", area);
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>

#define LEAP_YEAR(y) leap=((y%400==0)||(y%4==0&&y%100!=0)?'L':'N');

int main() {
    int y;
    scanf("%d", &y);
    char leap;
    LEAP_YEAR(y);
    printf("%c", leap);
    return 0;
}
```

5.代码如下：
```c
#include <stdio.h>

#define OUTPUT(n) for(int i=1;i<=3;i++){for(int j=1;j<=i;j++){printf("%6.2f",n);}printf("\n");}

int main() {
    double n;
    scanf("%lf", &n);
    OUTPUT(n);
    return 0;
}
```

6.代码如下：
```c
#include <stdio.h>

#define MAX(a,b,c) max=(a>b&&a>c)?a:(b>a&&b>c)?b:c;

double max_fun(double a, double b, double c) {
    return (a>b&&a>c)?a:(b>a&&b>c)?b:c;
}

int main() {
    double a, b, c, max;
    scanf("%lf %lf %lf", &a, &b, &c);
    MAX(a, b, c);
    printf("%.3lf\n%.3lf", max_fun(a,b,c), max);
    return 0;
}
```

7.代码如下：
```c
#include <stdio.h>
#include <string.h>

#define NEXT(line,len) for(int i=0; i<len; i++){if(line[i]>='a'&&line[i]<='z'){line[i]=(line[i]-'a'+1)%26+'a';}if(line[i]>='A'&&line[i]<='Z'){line[i]=(line[i]-'A'+1)%26+'A';}}

int main() {
    char line[1000];
    // 读一行
    scanf("%[^\n]", &line);
    int len = strlen(line);
    NEXT(line, len);
    printf("%s", line);
    return 0;
}
```

- [下一章](/Chapter8.md)
- [返回目录](/README.md)
