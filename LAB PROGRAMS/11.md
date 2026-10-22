#include <stdio.h>
#include <string.h>

struct Symbol {
    char name[30];
    int address;
};

struct Symbol table[50];
int count = 0;

int search(char name[]) {
    int i;
    for (i = 0; i < count; i++)
        if (strcmp(table[i].name, name) == 0)
            return i;
    return -1;
}

int main() {
    int choice, address, pos;
    char name[30];

    while (1) {
        scanf("%d", &choice);

        if (choice == 1) {
            scanf("%29s%d", name, &address);
            if (count >= 50)
                printf("Table full\n");
            else if (search(name) != -1)
                printf("Duplicate symbol\n");
            else {
                strcpy(table[count].name, name);
                table[count].address = address;
                count++;
                printf("Inserted\n");
            }
        } else if (choice == 2) {
            for (int i = 0; i < count; i++)
                printf("%s %d\n", table[i].name, table[i].address);
        } else if (choice == 3) {
            scanf("%29s", name);
            pos = search(name);
            if (pos == -1)
                printf("Symbol not found\n");
            else
                printf("Symbol found: %s %d\n", table[pos].name, table[pos].address);
        } else if (choice == 4) {
            scanf("%29s%d", name, &address);
            pos = search(name);
            if (pos == -1)
                printf("Symbol not found\n");
            else {
                table[pos].address = address;
                printf("Modified\n");
            }
        } else if (choice == 5) {
            break;
        } else {
            printf("Invalid choice\n");
        }
    }

    return 0;
}


<img width="958" height="452" alt="image" src="https://github.com/user-attachments/assets/7217a60d-b7c0-41cb-8db9-61c869c2b125" />
