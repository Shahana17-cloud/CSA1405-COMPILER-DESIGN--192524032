#include <stdio.h>
#include <string.h>

int main(void) {
    char s[100];
    int i = 0, a = 0, b = 0, valid = 1;

    scanf("%99s", s);

    while (s[i] == 'a') {
        a++;
        i++;
    }

    while (s[i] == 'b') {
        b++;
        i++;
    }

    if (s[i] != '\0' || a == 0 || b == 0)
        valid = 0;

    if (valid)
        printf("String accepted\n");
    else
        printf("String not accepted\n");

    return 0;
}

<img width="338" height="70" alt="image" src="https://github.com/user-attachments/assets/8b82201e-eb3f-4efc-8138-41b438a1d419" />
