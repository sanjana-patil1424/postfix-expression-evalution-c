# postfix-expression-evalution-c
To design, develop, and implement a C program to evaluate a postfix expression containing single-digit operands and the operators + , - , * , / , % , ^ using a stack.

## Description

Postfix expression evaluation is a classic stack application.
In postfix notation (Reverse Polish Notation), operators follow operands, so parentheses are not required.

The program scans the postfix expression from left to right:

Operands are pushed onto the stack.

When an operator is encountered, the top two operands are popped, the operation is performed, and the result is pushed back onto the stack.

At the end of evaluation, the stack contains one value, which is the final result.

## Algorithm

Initialize an empty stack.

Read the postfix expression.

Scan the expression character by character.

If the character is an operand (digit):

Convert it to integer.

Push it onto the stack.

If the character is an operator:

Pop two operands from the stack.

Apply the operator.

Push the result back onto the stack.

After scanning the expression, pop the final result.

Display the result.

## Program (C Implementation)

#include <stdio.h>
#include <ctype.h>
#include <math.h>

#define MAX 50

int stack[MAX];
int top = -1;

/* Push operation */
void push(int value) {
    stack[++top] = value;
}

/* Pop operation */
int pop() {
    return stack[top--];
}

int main() {
    char postfix[MAX];
    int i, operand1, operand2, result;

    printf("Enter Postfix Expression: ");
    scanf("%s", postfix);

    for (i = 0; postfix[i] != '\0'; i++) {

        /* If operand, push to stack */
        if (isdigit(postfix[i])) {
            push(postfix[i] - '0');
        }
        /* If operator, pop two operands */
        else {
            operand2 = pop();
            operand1 = pop();

            switch (postfix[i]) {
                case '+':
                    result = operand1 + operand2;
                    break;
                case '-':
                    result = operand1 - operand2;
                    break;
                case '*':
                    result = operand1 * operand2;
                    break;
                case '/':
                    result = operand1 / operand2;
                    break;
                case '%':
                    result = operand1 % operand2;
                    break;
                case '^':
                    result = pow(operand1, operand2);
                    break;
            }
            push(result);
        }
    }

    printf("Result = %d\n", pop());
    return 0;
}

## Sample Input and Output
## Input:
23*54*+9-

## Output:
17

## Applications

Expression evaluation in compilers

Calculator implementations

Stack-based problem solving

Understanding postfix notation

## Conclusion

The program successfully evaluates a postfix expression using a stack data structure.
It demonstrates efficient use of stacks for expression evaluation without requiring parentheses or precedence rules.

## Author
Sanjana Patil
