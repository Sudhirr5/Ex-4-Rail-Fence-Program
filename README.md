# Ex- 5 - IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE
### Name : R. SUDHIR KUMAR
### Register number : 212223230221

# AIM:
To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:
In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:
STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```c
#include <stdio.h>
#include <string.h>
void encryptRailFence(char *message, int rails)
{
    int len = strlen(message);
    if (rails == 1)
    {
        printf("Encrypted text: %s\n", message);
        return;
    }
    char rail[rails][len];
    for (int i = 0; i < rails; i++)
        for (int j = 0; j < len; j++)
            rail[i][j] = '\n';
    int row = 0, direction = 1;
    for (int i = 0; i < len; i++)
    {
        rail[row][i] = message[i];
        row += direction;
        if (row == rails - 1 || row == 0)
            direction = -direction;
    }
    printf("Encrypted text: ");
    for (int i = 0; i < rails; i++)
    {
        for (int j = 0; j < len; j++)
        {
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);
        }
    }
    printf("\n");
}
int main()
{
    char message[100];
    int rails;
    printf("Enter a Secret Message: ");
    scanf(" %[^\n]", message);
    printf("Enter number of rails: ");
    scanf("%d", &rails);
    encryptRailFence(message, rails);
    return 0;
}
```

# OUTPUT
<img width="370" height="181" alt="Screenshot 2026-08-01 084410" src="https://github.com/user-attachments/assets/110b4d90-2db1-48c9-84a3-b711f12b8410" />

# RESULT
Thus,the program is verified successfully.
