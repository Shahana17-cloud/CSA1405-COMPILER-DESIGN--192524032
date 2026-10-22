#include <stdio.h>

int main() {
    int a, b, c;

    scanf("%d %d %d", &a, &b, &c);

    if (a >= b) {
        if (a >= c) {
            printf("Largest = %d\n", a);
        } else {
            printf("Largest = %d\n", c);
        }
    } else {
        if (b >= c) {
            printf("Largest = %d\n", b);
        } else {
            printf("Largest = %d\n", c);
        }
    }

    return 0;
}
<img width="956" height="450" alt="image" src="https://github.com/user-attachments/assets/6721477c-2f75-4772-a1ab-533b6a51ba04" />
