#include <stdio.h>
#include <stdlib.h>

void clearInputBuffer() {
    while (getchar() != '\n');
}

void displayMenu() {
    printf("\n--- Simple Calculator ---\n");
    printf("Select an operator:\n");
    printf("1. Addition (+)\n");
    printf("2. Subtraction (-)\n");
    printf("3. Multiplication (*)\n");
    printf("4. Division (/)\n");
    printf("5. Exit\n");
    printf("Enter your choice[1/2/3/4/5]: ");
}

int main() {
    char choice, continueChoice;
    double firstNumber, secondNumber, result;

    while (1) {
        displayMenu();
        choice = getchar();
        clearInputBuffer(); // clear the input buffer to handle any leftover characters

        if (choice == '5') {
            printf("Exiting the program. Goodbye!\n");
            break;
        }

        printf("Enter first number: ");
        while (scanf("%lf", &firstNumber) != 1) {
            printf("Invalid input! Please enter a valid number: ");
            clearInputBuffer();
        }
        clearInputBuffer();

        printf("Enter second number: ");
        while (scanf("%lf", &secondNumber) != 1) {
            printf("Invalid input! Please enter a valid number: ");
            clearInputBuffer();
        }
        clearInputBuffer();

        switch (choice) {
            case '1':
                result = firstNumber + secondNumber;
                printf("%.2lf + %.2lf = %.2lf\n", firstNumber, secondNumber, result);
                break;
            case '2':
                result = firstNumber - secondNumber;
                printf("%.2lf - %.2lf = %.2lf\n", firstNumber, secondNumber, result);
                break;
            case '3':
                result = firstNumber * secondNumber;
                printf("%.2lf * %.2lf = %.2lf\n", firstNumber, secondNumber, result);
                break;
            case '4':
                if (secondNumber != 0) {
                    result = firstNumber / secondNumber;
                    printf("%.2lf / %.2lf = %.2lf\n", firstNumber, secondNumber, result);
                } else {
                    printf("Error! Division by zero.\n");
                }
                break;
            default:
                printf("Error! Invalid choice. Please select a valid option.\n");
                break;
        }

        // Ask the user if they want to solve another problem
        printf("Do you want to solve another problem? (y/n): ");
        continueChoice = getchar();
        clearInputBuffer(); // clear the input buffer to handle any leftover characters

        if (continueChoice != 'y' && continueChoice != 'Y') {
            printf("Exiting the program. Goodbye!\n");
            break;
        }
    }

    return 0;
}
