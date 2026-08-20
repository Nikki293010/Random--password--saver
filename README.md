# Random--password--saver
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    char password[21];
    char characters[] =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        "abcdefghijklmnopqrstuvwxyz"
        "0123456789"
        "!@#$%^&*";

    int length = 12;
    int i;

    srand(time(NULL));

    // Generate random password
    for (i = 0; i < length; i++) {
        password[i] = characters[rand() % (sizeof(characters) - 1)];
    }

    password[length] = '\0';

    // Display password
    printf("Generated Password: %s\n", password);

    // Save password to file
    FILE *file = fopen("passwords.txt", "a");

    if (file == NULL) {
        printf("Error: Cannot open file.\n");
        return 1;
    }

    fprintf(file, "%s\n", password);
    fclose(file);

    printf("Password saved successfully in passwords.txt\n");

    return 0;
}

OUTPUT:

Generated Password: kT7@pL2#xQ9!
Password saved successfully in passwords.txt
kT7@pL2#xQ9!
