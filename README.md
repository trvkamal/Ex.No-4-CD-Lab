# Ex.No:4
# RECOGNITION OF A VALID VARIABLE WHICH STARTS WITH A LETTER FOLLOWED BY ANY NUMBER OF LETTERS OR DIGITS USING YACC
## Register Number: 212222240042
## Date: 30-09-2025

## Aim:
To write a YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits.

## ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the keywords int, float and double and for the identifier.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with YACC compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a statement as input and the valid variables are identified as output.
   
## PROGRAM

expr.l
```
%{
#include "expr4.tab.h"
%}

%%

[a-zA-Z][a-zA-Z0-9]*    { return VARIABLE; }
.|\n                    { return INVALID; }

%%
int yywrap() {
    return 1;
}
```
expr.y
```
%{
#include <stdio.h>
#include <stdlib.h>

int yylex(void);
void yyerror(const char *s);
%}

%token VARIABLE INVALID

%%

input:
    VARIABLE { printf("Valid variable name\n"); }
  | INVALID  { printf("Invalid variable name\n"); }
  ;

%%

int main() {
    printf("Enter a variable name: ");
    yyparse();
    return 0;
}

void yyerror(const char *s) {
    // we handle invalid input in the grammar, so this can stay empty
}
```
## Output

<img width="797" height="110" alt="Screenshot 2025-10-06 143035" src="https://github.com/user-attachments/assets/ec342a20-353c-4693-bdf8-a68ae87d2039" />

<img width="780" height="118" alt="Screenshot 2025-10-06 143043" src="https://github.com/user-attachments/assets/b26b3618-0fc4-4937-9bbf-564403ead681" />

## Result
A YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits is executed successfully and the output is verified.
