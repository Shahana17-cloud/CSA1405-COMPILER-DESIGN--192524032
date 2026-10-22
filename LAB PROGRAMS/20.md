#include <stdio.h>
#include <string.h>
#include <ctype.h>

char lhs[] = {'E', 'E', 'T', 'T', 'F', 'F'};
char *rhs[] = {"E+T", "T", "T*F", "F", "(E)", "i"};
char nt[] = {'E', 'T', 'F'};
int trailing[3][128];

int indexOf(char c) {
    int i;
    for (i = 0; i < 3; i++)
        if (nt[i] == c)
            return i;
    return -1;
}

int main(void) {
    int i, j, changed, len;
    char c;
    char order[] = "+*()i";

    do {
        changed = 0;

        for (i = 0; i < 6; i++) {
            int a = indexOf(lhs[i]);
            len = strlen(rhs[i]);
            c = rhs[i][len - 1];

            if (!isupper((unsigned char)c)) {
                if (!trailing[a][(unsigned char)c]) {
                    trailing[a][(unsigned char)c] = 1;
                    changed = 1;
                }
            } else {
                int b = indexOf(c);

                if (len >= 2 &&
                    !isupper((unsigned char)rhs[i][len - 2])) {
                    c = rhs[i][len - 2];
                    if (!trailing[a][(unsigned char)c]) {
                        trailing[a][(unsigned char)c] = 1;
                        changed = 1;
                    }
                }

                for (j = 0; j < 128; j++) {
                    if (trailing[b][j] && !trailing[a][j]) {
                        trailing[a][j] = 1;
                        changed = 1;
                    }
                }
            }
        }
    } while (changed);

    for (i = 0; i < 3; i++) {
        printf("TRAILING(%c) = { ", nt[i]);

        for (j = 0; order[j] != '\0'; j++) {
            c = order[j];
            if (trailing[i][(unsigned char)c])
                printf("%c ", c);
        }

        printf("}\n");
    }

    return 0;
}
<img width="339" height="120" alt="image" src="https://github.com/user-attachments/assets/7e372f78-aaf7-4b30-bc25-8c55917b2831" />
