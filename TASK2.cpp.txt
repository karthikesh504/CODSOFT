// You are using GCC
#include<bits/stdc++.h>
using namespace std;
int main() {
    
    double num1, num2;
    char ch;

    cout << "Enter first number: ";
    cin >> num1;

    cout << "Enter an operator (+, -, *, /): ";
    cin >> ch;

    cout << "Enter second number: ";
    cin >> num2;
    
    
    switch(ch) {
        case '+':
            cout << "Result: " << num1 + num2 << "\n";
            break;
        case '-':
            cout << "Result: " << num1 - num2 << "\n";
            break;
        case '*':
            cout << "Result: " << num1 * num2 << "\n";
            break;
        case '/':
            if (num2 != 0) {
                cout << "Result: " << num1 / num2 << "\n";
            } else {
                cout << "Error: Division by zero is not allowed.\n";
            }
            break;
        default:
            std::cout << "Invalid operator.\n";
            break;
    }
    return 0;
}
