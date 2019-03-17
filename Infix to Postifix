#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>
#define MAX 100
struct stack
{
	int top;
	char item[MAX];

};
struct stack opstack;
void push(char);
char pop();
void infixtopostfix(char infix[],char postfix[]);
int prcd(char, char);
int right_asso(char);
int get_weight(char);
char stacktop();
int empty(void);
int main()
{
	opstack.top=-1;
    char in[100], po[100];
    printf("Enter any infix expression:");
    gets(in);
    infixtopostfix(in,po);
    printf("The corresponding postfix expression is:");
    puts(po);
    return 0;
}
void infixtopostfix(char infix[],char postfix[])
{
    int i,outpos=0;
    char topsymb,c;
    for(i=0;(c=infix[i])!='\0';i++)
    {
        if(isdigit(c)||isalpha(c))
            postfix[outpos++]=c;
        else if(c=='(')
              push(c);
        else if(c==')')
        {
            topsymb=pop();
            while(!empty()&&(topsymb!='('))
            {
                postfix[outpos++]=topsymb;
                topsymb=pop();
            }
        }
        else
        {
            topsymb=stacktop();
            while(!empty()&&topsymb!='('&&prcd(topsymb,c))
            {
                topsymb=pop();
                postfix[outpos++]=topsymb;
                topsymb=stacktop();
            }
            push(c);
        }

    }
    while(!empty())
    {
        postfix[outpos++]=pop();

    }
    return;
}
int prcd(char op1, char op2)
{
    int op1_weight,op2_weight;
    op1_weight=get_weight(op1);
    op2_weight=get_weight(op2);
    if(op1_weight==op2_weight)
    {
        if(right_asso(op1))
            return (0);
        else
            return (1);
    }
    else if(op1_weight>op2_weight)
        return(1);
    else return(0);
}
int right_asso(char op)
{
    if(op=='^')
        return(1);
    else
        return(0);
}
int get_weight(char op)
{
    switch(op)
    {
        case '+':
        case '-': return (1);
        case '*':
        case '/': return (2);
        case '^': return (3);
        default : printf("illegal operation!");
        exit(1);
    }
}
void push(char symb)
{
    if(opstack.top==(MAX-1))
    {
        printf("\n Stack Overflow");
    }
    else
    {
        opstack.top++;
        opstack.item[opstack.top]=symb;
    }
}
char pop()
{
    char val;
    if(opstack.top==-1)
    {
        printf("\n Stack underflow");
    }
    else
    {
       val=opstack.item[opstack.top];
       opstack.top--;
    }
    return val;
}
char stacktop()
{
    return(opstack.item[opstack.top]);
}
int empty(void)
{
    if(opstack.top==-1)
        return (1);
    else
        return (0);
}


