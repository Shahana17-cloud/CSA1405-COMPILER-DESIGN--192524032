#include <stdio.h>
#include <string.h>

int main() {
    char gram[100];
    char part1[50], part2[50];
    char prefix[50], suffix1[50], suffix2[50];
    int i, j, k, pos;

    scanf("%99s", gram);

    i = 0;
    while (gram[i] != '|' && gram[i] != '\0') {
        part1[i] = gram[i];
        i++;
    }
    part1[i] = '\0';

    if (gram[i] != '|') {
        printf("Invalid production\n");
        return 0;
    }

    j = 0;
    i++;
    while (gram[i] != '\0') {
        part2[j++] = gram[i++];
    }
    part2[j] = '\0';

    i = 0;
    while (part1[i] != '\0' && part2[i] != '\0' &&
           part1[i] == part2[i]) {
        prefix[i] = part1[i];
        i++;
    }
    prefix[i] = '\0';
    pos = i;

    if (pos == 0) {
        printf("No common prefix found\n");
        return 0;
    }

    strcpy(suffix1, part1 + pos);
    strcpy(suffix2, part2 + pos);

    printf("S->%sX\n", prefix);
    printf("X->%s|%s\n", suffix1, suffix2);

    return 0;
}
<img width="959" height="446" alt="image" src="https://github.com/user-attachments/assets/02a26a1c-f58e-4b1a-a4a9-505183335544" />
