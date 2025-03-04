#include <stdio.h>
#include <math.h>

double addition(double, double);
double subtraction(double , double );
double multiplication(double , double );
double division(double, double);
int modulus(int, int);
double exponentiation(double, double);
double square_root(double);
double getNum(void);
void menu(void);

int main(void) {
    menu();
    return 0;
}
double addition(double first, double second) {
    return first + second;
}

double subtraction(double first, double second) {
    return first - second;
}

double multiplication(double first, double second) {
    return first * second;
}

double division(double first, double second) {
    if (second == 0) {
        printf("Mistake you can't make division on 0 ");
        return 0;
    }
    return first / second;
}

int modulus(int first, int second) {
    if (second == 0) {
        printf("Mistake");
        return 0;
    }
    return first % second;
}

double exponentiation(double base, double exp) {
    return pow(base, exp);
}

double square_root(double num) {
    if (num < 0) {
        printf("Mistake you cant take squareroot from negative number ");
        return -1;
    }
    return sqrt(num);
}

double getNum(void) {
    char record[121] = { 0 };
    double number = 0.0;
    fgets(record, 121, stdin);
    if (sscanf_s(record, "%lf", &number) != 1) {
        number = -1.0;
    }
    return number;
}

void menu(void) {
    int choice;
    int number1, number2;
    do {
        printf("--- Enhanced Calculator ---\n");
        printf("Choose operation\n");
        printf("1.Addition: (+)\n"); 
        printf("2.Subtraction: (-)\n");
        printf("3.Multiplication: (*)\n");
        printf("4.Division: (/)\n"); 
        printf("5.Modulus: (percent)\n");
        printf("6.Exponentiation: (^)\n");
        printf("7.Square root: (r)\n");
        printf("8. Exit: (e)\n");
        printf("Choose operation:\n");
        scanf_s("%d", &choice);
        int temp = getchar(); 
        if (choice >= 1 && choice <= 6) {
            printf("Enter first number: ");
            number1 = getNum();
            printf("Enter second number: ");
            number2 = getNum();


        }
        switch (choice)
        {
            case 1:
                printf("Result: %.2lf\n", addition(number1,number2));
                break;
            case 2:
                printf("Result: %.2lf\n", subtraction(number1, number2));
                break;
            case 3:
                printf("Result: %.2lf\n", multiplication(number1 , number2));
                break;
            case 4:
                printf("Result: %.2lf\n", division(number1 , number2));
                break;
            case 5:
                printf("Result: %d\n", modulus((int)number1, (int)number2));
                break;
            case 6:
                printf("Result: %.2lf\n", exponentiation(number1, number2));
                break;
            case 7:
                printf("Enter: ");
                number1 = getNum();
                printf("Result: %.2lf\n", square_root(number1));
                break;
            case 8:
                printf("Exit the program: ");
                break;

            default:
                printf("Mistake: Wrong choice:\n");
        }
    } while (choice != 8);
}
