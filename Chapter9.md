# 第九章

1.代码如下：
```c
#include <stdio.h>

struct date {
    int year;
    int month;
    int day;
};

int main() {
    struct date d;
    scanf("%d", &d.year);
    scanf("%d", &d.month);
    scanf("%d", &d.day);
    int month_days[13] = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    if (d.year % 400 == 0 || (d.year % 4 == 0 && d.year % 100 != 0)) {
        month_days[2]++;
    }
    int sum = 0;
    for (int i = 1; i < d.month; i++) {
        sum += month_days[i];
    }
    sum += d.day;
    printf("%d", sum);
    return 0;
}
```

2.代码如下：
```c
#include <stdio.h>

typedef struct student Student;

struct student  {
    char id[30];
    char name[30];
    int score[3];
};

int main() {
    int i, j, n;
    scanf("%d", &n);
    Student students[n];
    for (i = 0; i < n; i++) {
        scanf("%s %s", students[i].id, students[i].name);
        for (j = 0; j < 3; j++) {
            scanf("%d", &students[i].score[j]);
        }
    }
    for (i = 0; i < n; i++) {
        printf("%s,%s,%d,%d,%d\n", students[i].id, students[i].name, students[i].score[0], students[i].score[1], students[i].score[2]);
    }
    return 0;
}
```

3.代码如下(写的有点啰嗦)：
```c
#include <stdio.h>
#include <stdlib.h>

struct student  {
    char id[30];
    char name[30];
    int score[3];
    double sum; // 平均成绩
};

typedef struct student Student;

void sumScore(Student *s, int n) {
    int sum = 0;
    for (int i = 0; i < 3; i++) {
        sum += s->score[i];
    }
    s->sum = sum/3.0;
}

int cmp(const void *a,const void *b){
    Student pa = *(Student*)a, pb = *(Student*)b;
    int grade_cmp = pa.sum > pb.sum ? 1 : pa.sum == pb.sum ? 0 : -1;
    if (grade_cmp == 0) {
        return pa.id - pb.id;
    }
    return -grade_cmp;
}

int main() {
    int i, j, n;
    scanf("%d", &n);
    Student students[n];
    for (i = 0; i < n; i++) {
        scanf("%s %s", students[i].id, students[i].name);
        for (j = 0; j < 3; j++) {
            scanf("%d", &students[i].score[j]);
        }
        sumScore(&students[i], n);
    }
    double sum1 = 0, sum2 = 0, sum3 = 0;
    for (i = 0; i < n; i++) {
        sum1 += students[i].score[0];
        sum2 += students[i].score[1];
        sum3 += students[i].score[2];
    }
    printf("%d %d %d\n", (int)(sum1/n), (int)(sum2/n), (int)(sum3/n));
    qsort(students, n, sizeof(Student), cmp);
    printf("%s %s %d %d %d\n", students[0].id, students[0].name, students[0].score[0], students[0].score[1], students[0].score[2]);
    return 0;
}
```

4.代码如下：
```c
#include <stdio.h>
#include <stdlib.h>

typedef struct student Student;

struct student  {
    int id;
    int grade;
    Student *next;
};

Student *merge(Student *a, Student *b, int a_len, int b_len) {
    Student *list, *temp, *newNode; // 链表指针、链表临时最后一个元素指针、新结点指针
    int flag_a[a_len], flag_b[b_len], ptr_a = 0, ptr_b = 0, min_a = a->id, min_b = b->id, i, j, a_continue = 0,
        b_continue = 0, grade_a = a->grade, grade_b = b->grade;
    for (i = 0; i < a_len; i++) {
        flag_a[i] = 0;
    }
    for (i = 0; i < b_len; i++) {
        flag_b[i] = 0;
    }
    for (i = 1; i < a_len; i++) {
        if (a[i].id < min_a && !flag_a[i]) {
            ptr_a = i;
            min_a = a[i].id;
            grade_a = a[i].grade;
        }
    }
    for (i = 1; i < b_len; i++) {
        if (b[i].id < min_b && !flag_b[i]) {
            ptr_b = i;
            min_b = b[i].id;
            grade_b = b[i].grade;
        }
    }
    if (min_a < min_b) {
        list = malloc(sizeof(Student));
        list->id = min_a;
        list->grade = grade_a;
        flag_a[ptr_a] = 1;
    } else {
        list = malloc(sizeof(Student));
        list->id = min_b;
        list->grade = grade_b;
        flag_b[ptr_b] = 1;
    }
    temp = list;
    for (i = 1; i < a_len+b_len; i++) {
        // 找到新的初始ptr_a
        for (j = 0; j < a_len; j++) {
            if (!flag_a[j]) {
                a_continue = 1;
                ptr_a = j;
                min_a = a[j].id;
                grade_a = a[j].grade;
                break;
            }
        }
        // 找到新的初始ptr_b
        for (j = 0; j < b_len; j++) {
            if (!flag_b[j]) {
                b_continue = 1;
                ptr_b = j;
                min_b = b[j].id;
                grade_b = b[j].grade;
                break;
            }
        }
        // A没排完且B没排完
        if (a_continue && b_continue) {
            for (j = 0; j < a_len; j++) {
                if (a[j].id < min_a && !flag_a[j]) {
                    ptr_a = j;
                    min_a = a[j].id;
                    grade_a = a[j].grade;
                }
            }
            for (j = 0; j < b_len; j++) {
                if (b[j].id < min_b && !flag_b[j]) {
                    ptr_b = j;
                    min_b = b[j].id;
                    grade_b = b[j].grade;
                }
            }
            if (min_a < min_b) {
                newNode = malloc(sizeof(Student));
                newNode->id = min_a;
                newNode->grade = grade_a;
                flag_a[ptr_a] = 1;
            } else {
                newNode = malloc(sizeof(Student));
                newNode->id = min_b;
                newNode->grade = grade_b;
                flag_b[ptr_b] = 1;
            }
        } else if (a_continue) {    // 只剩A
            for (j = 0; j < a_len; j++) {
                if (a[j].id < min_a && !flag_a[j]) {
                    ptr_a = j;
                    min_a = a[j].id;
                    grade_a = a[j].grade;
                }
            }
            newNode = malloc(sizeof(Student));
            newNode->id = min_a;
            newNode->grade = grade_a;
            flag_a[ptr_a] = 1;
        } else {                    // 只剩B
            for (j = 0; j < b_len; j++) {
                if (b[j].id < min_b && !flag_b[j]) {
                    ptr_b = j;
                    min_b = b[j].id;
                    grade_b = b[j].grade;
                }
            }
            newNode = malloc(sizeof(Student));
            newNode->id = min_b;
            newNode->grade = grade_b;
            flag_b[ptr_b] = 1;
        }
        temp->next = newNode;
        temp = newNode;
        a_continue = 0;
        b_continue = 0;
    }
    return list;
}

int main() {
    int i, j, n, m;
    scanf("%d %d", &n, &m);
    Student s1[n], s2[m], *s3, *p;
    for (i = 0; i < n; i++) {
        scanf("%d %d", &s1[i].id, &s1[i].grade);
    }
    for (i = 0; i < m; i++) {
        scanf("%d %d", &s2[i].id, &s2[i].grade);
    }
    s3 = merge(s1, s2, n, m);
    p = s3;
    for (i = 0; i < n+m; i++) {
        printf("%d %d\n", p->id, p->grade);
        p = p->next;
    }
    return 0;
}
```

- [返回目录](/README.md)
