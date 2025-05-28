# DS_Module13

## AIM: 
~~~
To Implement the program for applications of stack using c program.
Applications of stacks are :
1)conversion of Infix to Postfix expression
2)Evaluation of Post fix Expression & Tower of Hanoi
3)Evaluation of Pre fix Expression
~~~
## PROGRAMS:
### 1)Conversion of Infix to Postfix expression
```
char IntoPost(char *exp)
{
    char *e,x;
    e = exp;
  while(*e != '\0')
    {
        if(isalnum(*e))
            printf("%c",*e);
        else if(*e == '(')
            push(*e);
        else if(*e == ')')
        {
            while((x = pop()) != '(')
                printf("%c", x);
        }
        else
        {
            while(priority(stack[top]) >= priority(*e))
                printf("%c",pop());
            push(*e);
        }
        e++;
    }
    
    while(top != -1)
    {
        printf("%c",pop());
    } 
    return 1;
}
```
### 2)Evaluation of Post fix Expression & Tower of Hanoi
```
a)post fix Expression
#include<stdio.h>
#include<ctype.h>
int stack[20];
int top = -1;

void push(int x)
{
    stack[++top] = x;
}

int pop()
{
    return stack[top--];
}

void evalpostfix(char *e)
{
    while(*e != '\0')
    {
        int n,a,b,c;
        if(isdigit(*e))
        {
            n=*e-48;
            push(n);
        }
        else
        {
            a=pop();
            b=pop();
            switch(*e)
            {
                case '+':
                {
                    c=a+b;
                    break;
                }
                case '-':
                {
                    c=b-a;
                    break;
                }
                case '*':
                {
                    c=a*b;
                    break;
                }
                case '/':
                {
                    c=b/a;
                    break;
                }
            }
            push(c);
        }
        ++e;
        
    }
    printf("%d",pop());
}

b)Tower of Hanoi
#include<stdio.h>
void TOH(int n,char x,char y,char z)
{
    if(n>0)
    {
        TOH(n-1,x,z,y);
        printf("%c to %c\n",x,y);
        TOH(n-1,z,y,x);
    }
}
```
### Evaluation of Prefix Expression 
```


#include<stdio.h>
#include<string.h>
#include<ctype.h>

int s[50];
int top=0;

void push(int ch)
{
	s[++top]=ch;
}

int pop()
{
	return s[top--];
}

void evalprefix(char p[50])
{
    int i=strlen(p)-1;
    while(i>=0)
    {
        if(isdigit(p[i]))
        {
            push(p[i]-48);
        }
        else
        {
            int a,b,c;
            a=pop();
            b=pop();
            switch(p[i])
            {
                case '+':
                {
                    c=a+b;
                    break;
                }
                case '/':
                {
                    c=b/a;
                    break;
                }
                case '-':
                {
                    c=a-b;
                    break;
                }
                case '*':
                {
                    c=a*b;
                    break;
                }
            }
            push(c);
        }
        i--;
    }
    printf("%d",pop());
}


```
## OUTPUT 
### Conversion of Infix to Postfix expression
![image](https://github.com/user-attachments/assets/c9f714d9-2807-40ca-9f09-0eb6a3d9f9ee)

### 2 a)Evaluation of Post fix Expression
![image](https://github.com/user-attachments/assets/cdbc6c65-3837-43fe-846c-a452d0ec42c4)

### 2 b)tower of hanoi
![image](https://github.com/user-attachments/assets/954b8ce5-22b3-43c1-bd44-028e1a6a3a71)
### Evaluation of Prefix Expression 
![image](https://github.com/user-attachments/assets/82edb7a1-2fd1-44cc-a9da-15111c8f1729)



