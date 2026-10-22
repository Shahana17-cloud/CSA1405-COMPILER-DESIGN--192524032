#include <stdio.h>
#include <string.h>

int main(void) {
    int n, i;
    char code[100];

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%99s", code);

        if (strlen(code) < 5 || code[1] != '=')
            continue;

        printf("MOV %c, R%d\n", code[2], i);

        if (code[4] == '+')
            printf("ADD %c, R%d\n", code[5], i);
        else if (code[4] == '-')
            printf("SUB %c, R%d\n", code[5], i);
        else if (code[4] == '*')
            printf("MUL %c, R%d\n", code[5], i);
        else if (code[4] == '/')
            printf("DIV %c, R%d\n", code[5], i);

        printf("MOV R%d, %c\n", i, code[0]);
    }
    <img width="229" height="188" alt="image" src="https://github.com/user-attachments/assets/f1fb202b-00e6-4766-8339-435582869b25" />


    return 0;
}
