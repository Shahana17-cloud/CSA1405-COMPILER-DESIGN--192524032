
#include <stdio.h>
#include <string.h>

char p[10][20];
int n;
int follow[26][26];

int main() {
    int i, j, k;
    char c;

    scanf("%d", &n);

    for (i = 0; i < n; i++)
        scanf("%s", p[i]);

    follow[p[0][0] - 'A']['$' - 'A'] = 0;

    for (i = 0; i < n; i++) {
        int a = p[i][0] - 'A';

        for (j = 2; p[i][j] != '\0'; j++) {
            c = p[i][j];

            if (c >= 'A' && c <= 'Z') {
                if (p[i][j + 1] != '\0') {
                    char next = p[i][j + 1];

                    if (next >= 'a' && next <= 'z')
                        follow[c - 'A'][next - 'A'] = 1;
                }
            }
        }
    }

    for (i = 0; i < n; i++) {
        int a = p[i][0] - 'A';

        for (j = 2; p[i][j] != '\0'; j++) {
            if (p[i][j] >= 'A' && p[i][j] <= 'Z') {
                if (p[i][j + 1] == '\0' && p[i][j] != p[i][0]) {
                    for (k = 0; k < 26; k++)
                        if (follow[a][k])
                            follow[p[i][j] - 'A'][k] = 1;
                }
            }
        }
    }

    scanf(" %c", &c);

    printf("FOLLOW(%c) = { ", c);

    if (c == p[0][0])
        printf("$ ");

    for (i = 0; i < n; i++) {
        int a = p[i][0] - 'A';

        for (j = 2; p[i][j] != '\0'; j++) {
            if (p[i][j] == c && p[i][j + 1] >= 'a' && p[i][j + 1] <= 'z')
                printf("%c ", p[i][j + 1]);
        }
    }

    printf("}\n");
    return 0;
}
<img width="959" height="443" alt="Screenshot 2026-10-22 132423" src="https://github.com/user-attachments/assets/564945ac-3f55-4188-95f5-a7ba3be201c2" />
<img width="959" height="443" alt="image" src="https://github.com/user-attachments/assets/9cb97b66-b7ca-4f27-8b2f-37e82b93d456" />
