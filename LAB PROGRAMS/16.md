#include <stdio.h>
#include <string.h>

int main(void) {
    char out[20], a[20], op, b[20], nextOp;
    char temp[20];
    int n = 1;

    scanf("%19s = %19s %c %19s", out, a, &op, b);

    if (op != '+' && op != '-') {
        printf("Unsupported operator\n");
        return 0;
    }

    sprintf(temp, "t%d", n++);
    printf("%s=%s%c%s\n", temp, a, op, b);

    while (scanf(" %c %19s", &nextOp, b) == 2) {
        if (nextOp != '+' && nextOp != '-')
            break;

        strcpy(a, temp);
        sprintf(temp, "t%d", n++);
        printf("%s=%s%c%s\n", temp, a, nextOp, b);
    }

    printf("%s=%s\n", out, temp);

    return 0;
}

<img width="329" height="159" alt="image" src="https://github.com/user-attachments/assets/375ff265-6e9c-4529-83cf-7ce3e93f3f0b" />
