#include <stdio.h>
#include <string.h>
#include <ctype.h>

char s[100];
int pos;

int E(void);

int F(void) {
    if (s[pos] == '(') {
        pos++;
        if (!E() || s[pos] != ')')
            return 0;
        pos++;
        return 1;
    }

    if (isalnum((unsigned char)s[pos])) {
        while (isalnum((unsigned char)s[pos]))
            pos++;
        return 1;
    }

    return 0;
}

int T(void) {
    if (!F())
        return 0;

    while (s[pos] == '*' || s[pos] == '/') {
        pos++;
        if (!F())
            return 0;
    }
    return 1;
}

int E(void) {
    if (!T())
        return 0;

    while (s[pos] == '+' || s[pos] == '-') {
        pos++;
        if (!T())
            return 0;
    }
    return 1;
}

int main(void) {
    scanf("%99s", s);
    pos = 0;

    if (E() && s[pos] == '\0')
        printf("Accepted\n");
    else
        printf("Not Accepted\n");

    return 0;
}

<img width="398" height="108" alt="image" src="https://github.com/user-attachments/assets/70751b8d-520a-4de9-bac1-25b21bfdfda2" />
