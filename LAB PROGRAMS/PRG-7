#include <stdio.h>
#include <ctype.h>

void FIRST(char result[], char c);
void addToResultSet(char result[], char val);

int numOfProductions;
char productionSet[10][10];

int main()
{
    int i;
    char choice;
    char c;
    char result[20];

    printf("How many productions? : ");
    scanf("%d", &numOfProductions);

    for (i = 0; i < numOfProductions; i++)
    {
        printf("Enter production %d: ", i + 1);
        scanf("%s", productionSet[i]);
    }

    do
    {
        result[0] = '\0';

        printf("\nFind the FIRST of: ");
        scanf(" %c", &c);

        FIRST(result, c);

        printf("FIRST(%c) = { ", c);

        for (i = 0; result[i] != '\0'; i++)
        {
            printf("%c ", result[i]);
        }

        printf("}\n");

        printf("Press 'y' to continue: ");
        scanf(" %c", &choice);

    } while (choice == 'y' || choice == 'Y');

    return 0;
}

void FIRST(char result[], char c)
{
    int i, j, k;
    char subResult[20];
    int foundEpsilon;

    subResult[0] = '\0';

    /*
       If c is a terminal,
       FIRST(c) = {c}
    */
    if (!isupper(c))
    {
        addToResultSet(result, c);
        return;
    }

    /*
       If c is a non-terminal,
       check all productions.
    */
    for (i = 0; i < numOfProductions; i++)
    {
        if (productionSet[i][0] == c)
        {
            /*
               If X -> epsilon,
               add epsilon to FIRST(X).
            */
            if (productionSet[i][2] == '$')
            {
                addToResultSet(result, '$');
            }
            else
            {
                j = 2;

                while (productionSet[i][j] != '\0')
                {
                    foundEpsilon = 0;

                    FIRST(subResult, productionSet[i][j]);

                    for (k = 0; subResult[k] != '\0'; k++)
                    {
                        addToResultSet(result, subResult[k]);
                    }

                    for (k = 0; subResult[k] != '\0'; k++)
                    {
                        if (subResult[k] == '$')
                        {
                            foundEpsilon = 1;
                            break;
                        }
                    }

                    if (!foundEpsilon)
                    {
                        break;
                    }

                    j++;
                }
            }
        }
    }
}

void addToResultSet(char result[], char val)
{
    int k;

    for (k = 0; result[k] != '\0'; k++)
    {
        if (result[k] == val)
        {
            return;
        }
    }

    result[k] = val;
    result[k + 1] = '\0';
}
