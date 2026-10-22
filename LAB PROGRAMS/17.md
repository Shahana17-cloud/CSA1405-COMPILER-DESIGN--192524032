#include <stdio.h>
#include <ctype.h>

int main(void) {
    int c, characters = 0, words = 0, lines = 0;
    int inWord = 0, hasContent = 0, last = '\0';

    while ((c = getchar()) != EOF && c != '~') {
        characters++;
        hasContent = 1;
        last = c;

        if (c == '\n')
            lines++;

        if (isspace((unsigned char)c)) {
            inWord = 0;
        } else if (!inWord) {
            words++;
            inWord = 1;
        }
    }

    if (hasContent && last != '\n')
        lines++;

    printf("Total number of words: %d\n", words);
    printf("Total number of lines: %d\n", lines);
    printf("Total number of characters: %d\n", characters);

    return 0;
}
<img width="341" height="178" alt="image" src="https://github.com/user-attachments/assets/5a28dcf4-863b-41b5-b681-192f42de5a35" />
