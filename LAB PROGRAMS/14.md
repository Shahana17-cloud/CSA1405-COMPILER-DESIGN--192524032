#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main(void) {
    char s[100];
    int i, expectOperand = 1, valid = 1;

    scanf("%99s", s);

    for (i = 0; s[i] != '\0'; i++) {
        if (expectOperand) {
            if (isalnum((unsigned char)s[i])) {
                expectOperand = 0;
            } else {
                valid = 0;
                break;
            }
        } else {
            if (s[i] == '+' || s[i] == '-' ||
                s[i] == '*' || s[i] == '/') {
                expectOperand = 1;
            } else {
                valid = 0;
                break;
            }
        }
    }

    if (expectOperand)
        valid = 0;

    if (valid)
        printf("String accepted\n");
    else
        printf("String rejected\n");

    return 0;
}
<img width="419" height="67" alt="image" src="https://github.com/user-attachments/assets/4ca13ed3-8637-4c80-ae73-626d34927855" />
