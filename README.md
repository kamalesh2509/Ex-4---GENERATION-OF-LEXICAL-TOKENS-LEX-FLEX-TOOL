# Ex-4-GENERATION OF LEXICAL TOKENS LEX FLEX TOOL
# AIM
To write a lex program to implement lexical analyzer to recognize a few patterns.
## To write a lex program to implement lexical analyzer to recognize a few patterns.
# ALGORITHM

1.	Start the program.
2.	Lex program consists of three parts.

     a.	Declaration %%

  	b.	Translation rules %%

  	c.	Auxilary procedure.
4.	The declaration section includes declaration of variables, maintest, constants and regular definitions.
5.	Translation rule of lex program are statements of the form

     a.	P1 {action}

  	b.	P2 {action}

  	c.	…

  	d.	

  	e.	Pn {action}

7.	Write a program in the vi editor and save it with .l extension.
8.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l $ cc lex.yy.c
9.	Compile that file with C compiler and verify the output.
```
Name : E kamalesh
Reg No : 212222100019
```
# PROGRAM
```
/* program name is lexp.l */ 
%{ 
/* program to recognize a c program */ 
int COMMENT=0; 
%} 
identifier [a-zA-Z][a-zA-Z0-9]* 
%% 
#.* { printf("\n%s is a PREPROCESSOR DIRECTIVE",yytext);} 
int | 
float | 
char | 
double | 
while | 
for | 
do | 
if | 
break | 
continue | 
void | 
switch | 
case | 
long | 
struct | 
const | 
typedef | 
return | 
else | 
goto {printf("\n\t%s is a KEYWORD",yytext);} 
"/*" {COMMENT = 1;}  
"*/" {COMMENT = 0;} 
{identifier}\( {if(!COMMENT)printf("\n\nFUNCTION\n\t%s",yytext);} 
\{ {if(!COMMENT) printf("\n BLOCK BEGINS");} 
\} {if(!COMMENT) printf("\n BLOCK ENDS");} 
{identifier}(\[[0-9]*\])? {if(!COMMENT) printf("\n %s IDENTIFIER",yytext);} 
\".*\" {if(!COMMENT) printf("\n\t%s is a STRING",yytext);} 
[0-9]+ {if(!COMMENT) printf("\n\t%s is a NUMBER",yytext);} 
\)(\;)? {if(!COMMENT) printf("\n\t");ECHO;printf("\n");} 
\( ECHO; 
= {if(!COMMENT)printf("\n\t%s is an ASSIGNMENT OPERATOR",yytext);} 
\<= | 
\>= | 
\< | 
== | 
\> {if(!COMMENT) printf("\n\t%s is a RELATIONAL OPERATOR",yytext);} 
%% 
int main(int argc,char **argv) 
{ 
if (argc > 1) 
{ 
FILE *file; 
file = fopen(argv[1],"r"); 
if(!file) 
{ 
printf("could not open %s \n",argv[1]); 
exit(0); 
} 
yyin = file; 
} 
yylex(); 
printf("\n\n"); 

return 0; 
} int yywrap() 
{ 
return 0; 
}
```
# INPUT
```
#include<stdio.h> 
main() 
{ 
int a,b; 
}
```
# OUTPUT
![Screenshot 2024-04-29 110543](https://github.com/deesk13/Ex-4---GENERATION-OF-LEXICAL-TOKENS-LEX-FLEX-TOOL/assets/150927063/ffd58abf-0a5c-41b9-8f1e-11e5f8bb67e9)

# RESULT
## The lexical analyzer is implemented using lex and the output is verified.
