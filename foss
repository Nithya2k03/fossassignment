/* TO IMPLEMENT SIMPLE CALCULATOR USING LEX AND YACC
%{
#include <stdio.h>
#include <stdlib.h>
extern FILE *yyin;
%}
%union{
int i;
float f;
}
%left PLUS MINUS
%left MUL DIV
%right UMINUS
%token OPENB CLOSEB NEWLINE
%token <i> INTEGER
%token <f> FLOAT
%type <f> E
%%
S: E NEWLINE    {       printf("\nResult=%f\n", $1);
                        exit(0);
                };
E: E PLUS E     {       $$ = $1 + $3;
                        printf("\nE -> E + E");
                }
 | E MINUS E    {       $$ = $1 - $3;
                        printf("\nE -> E - E");
                }
 | UMINUS E     {       $$ = - $2;
                        printf("\nE -> - E");
                }
 | E MUL E      {       $$ = $1 * $3;
                        printf("\nE -> E * E");
                }
 | E DIV E      {       $$ = $1 * $3;
                        printf("\nE -> E / E");
                }
 | OPENB E CLOSEB       {       $$ = $2;
                                printf("\nE -> ( E )");
                        }
 | INTEGER      {       $$ = $1;
                        printf("\nE -> %d", $1);
                }
 | FLOAT        {       $$ = $1;
                        printf("\nE -> %f", $1);
                }
%%
int main()
{
        yyin = fopen("input.txt", "r");
        yyparse();
        return 0;
}
void yyerror(char *s)
{
        printf("\nError: %s\n", s);
}
