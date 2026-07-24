# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main()
{
    char text[100], rail[10][100];
    int rails, len, i, j, row = 0, direction = 1;

    printf("Enter the plaintext: ");
    fgets(text, sizeof(text), stdin);

    text[strcspn(text, "\n")] = '\0';

    printf("Enter the number of rails: ");
    scanf("%d", &rails);

    len = strlen(text);

    // Initialize the rail matrix
    for (i = 0; i < rails; i++)
    {
        for (j = 0; j < len; j++)
        {
            rail[i][j] = '\0';
        }
    }

    // Arrange characters in zigzag pattern
    for (i = 0; i < len; i++)
    {
        rail[row][i] = text[i];

        if (row == 0)
            direction = 1;
        else if (row == rails - 1)
            direction = -1;

        row = row + direction;
    }

    // Read row by row to get ciphertext
    printf("Ciphertext: ");

    for (i = 0; i < rails; i++)
    {
        for (j = 0; j < len; j++)
        {
            if (rail[i][j] != '\0')
                printf("%c", rail[i][j]);
        }
    }

    return 0;
}
```

# OUTPUT
<img width="942" height="272" alt="Screenshot 2026-07-24 110443" src="https://github.com/user-attachments/assets/9fbf0f1b-79e1-43a8-9f7c-dcf126c4d3b4" />

# RESULT
Thus, the Rail Fence Transposition Technique was successfully implemented using a C program.
