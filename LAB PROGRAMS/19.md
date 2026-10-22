#include <stdio.h>
#include <string.h>
#include <ctype.h>

char lhs[] = {'E', 'E', 'T', 'T', 'F', 'F'};
char *rhs[] = {"E+T", "T", "T*F", "F", "(E)", "i"};
char nt[] = {'E', 'T', 'F'};
int leading[3][128];

int indexOf(char c) {
    int i;
    for (i = 0; i < 3; i++)
        if (nt[i] == c)
            return i;
    return -1;
}

int main(void) {
    int i, j, changed;
    char c, d;

    do {
        changed = 0;

        for (i = 0; i < 6; i++) {
            int a = indexOf(lhs[i]);
            int b = indexOf(rhs[i][0]);

            if (b == -1) {
                c = rhs[i][0];
                if (!leading[a][(unsigned char)c]) {
                    leading[a][(unsigned char)c] = 1;
                    changed = 1;
                }
            } else {
                if (rhs[i][1] != '\0' &&
                    !isupper((unsigned char)rhs[i][1])) {
                    c = rhs[i][1];
                    if (!leading[a][(unsigned char)c]) {
                        leading[a][(unsigned char)c] = 1;
                        changed = 1;
                    }
                }

                for (j = 0; j < 128; j++) {
                    if (leading[b][j] && !leading[a][j]) {
                        leading[a][j] = 1;
                        changed = 1;
                    }
                }
            }
        }
    } while (changed);

    for (i = 0; i < 3; i++) {
        printf("LEADING(%c) = { ", nt[i]);
        for (j = 0; j < 128; j++)
            if (leading[i][j])
                printf("%c ", j);
        printf("}\n");
    }

    return 0;
}

<img width="347" height="172" alt="image" src="https://github.com/user-attachments/assets/94df10ac-0cca-4d58-9d0e-89f5635c066e" />
