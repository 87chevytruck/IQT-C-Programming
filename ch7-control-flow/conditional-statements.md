# conditional statements

### if statement

if statements create conditional jumps

tests an expression as TRUE or FALSE

when the expression is TRUE, the code block will be executed

```c
///minimum if statement syntax///

if (expression)
{
statement1;
}

///basic if statement examples///

if (1 > 0)               //example 1
{
printf("All is alright with the world. \n");
}

if (1)                  //example 2
{
printf("1 evaluates to TRUE. \n");
}

if (i  > u)  		 //example 3
{
printf("i is greater than u. (pun_intended = FALSE) \n");
}

if (i && i == u)         //example 4
{
printf("apparently, this works and i evaluates to TRUE. \n");
}

```

NOTE: do not leave if statements unwrapped, watch those { } !!



### if-else statements

an if statement may also include an else, these conditional statements test an expression as TRUE or FALSE

when the expression is TRUE the if code block will be executed...otherwise, the else code block is executed instead

```c
///if-else statement syntax///

if (expression)
{
    statement1;
}
else
{
    statement2;
}

///if-else statement examples///

if (i >= u)			//example 1 start
{
    printf("u is no greater than i. \n");
}
else
{
    printf("u is greater than i. \n");
}					//example 1 end

if (i && i == u)	//example 2 start
    printf("apparently, this works and i evaluates to true. \n");
else
    i = u			//example 2 end

/* set i equal to u since it's either 0 or not already equivalent */
```

NOTE: do not leave if-else statements unwrapped {}

### else-if statements

an if statement may also include multiple else conditions

else-if  statements tests an if expression as TRUE or FALSE

when the expression is TRUE, the if code block will be executed

when the expression is FALSE, the first else-if expression will be tested in turn

else-if expressions are tested for TRUE in turn

the else code block will be executed when the if and all else-if conditions are evaluated to false


an if statement may also check multiple conditions

```c
///else-if statement syntax///

if (expression1)
{
    statement1;
}
else if (expression2)
{
    statement2;
}
else
{
    statement3;
}

```

else-if example:

```c
///else-if statement examples///

if (i > u)
{
    printf("I is greater than u. \n");
}
else if (i < u)
{
    printf("u is greater than i. \n");
}
else
{
    printf("u and i are equal. \n");
}

```

NOTE: do note leave else-if statements unwrapped {}


### switch statements

switch statements also create conditional jumps

tests an expression or variable against cases

when the variable is equivalent to a case, the following statements will execute until a break

break statements, while optional, can be used to end cases

a switch case that does not end in a break statement will "fall through" and execute the following cases

NOTE: 
case labels must meet the following criteria

    -must be unique

    -ends with a COLON

    -have constants/constant expression

    -integral type (integer, character)

    -not a floating point number

    -a switch case should have at most one default label

    -default can be placed anywhere in the switch

    -break statement takes control out of the switch

    -two or more cases may share one break statement

    -nesting (switch within switch) is allowed

    -relational operators are NOT allowed in switch statement

    -Macro identifier are allowed as switch case label

    -const variable is allowed in switch case statements

    -empty switch case is allowed

switch statements also create conditional jumps

```c
///switch statement syntax///

switch (variable)
{
    case constant1:
            statement1;
            break;

    case constant2:
            statement2;
            break;

    default:
            statement3;
            break;
}

///switch statement examples///

switch (binaryInput)
{
    case 1:
            printf("%d = TRUE \n", binaryInput);
            break;
    case 0:
            printf("%d = FALSE \n", binaryInput);
            break;
    default:
            printf("something has gone wrong! \n");
            break;
}
```


>when do i use an IF statement?

whenever you have only ONE condition to act on (1)

```C
if (somethingIsTrue)
{
then_do_this_thing();			//one condition
}

/*i dont want to do anything if it's false */

```
>when do i use an IF-ELSE statement?


whenever you only have TWO conditions to act on (2)

```c
if (somethingIsTrue)
{
    then_do_this_thing();			//condition one
}
else
{
    otherwise_do_something_else();	//condition two
}

/*used for binary input validation, and error checking */

```
    
>when do i use an ELSE-IF statement?

whenever you have TWO OR MORE conditions to act on (2+)
    
```c
if (somethingIsTrue)
{
    then_do_this_thing();           //condition one
}
else if (somethingElseisTrue)
{
    then_do_this();                 //condition two
}
else
{
    otherwise_do_this_instead();	//condition three
}

```
    
>why should I use a SWITCH instead of ELSE-IF?

1.readability


```c
///switch////

switch (echoNumber)
{
    case 1:
            printf("one\n");
            break;
    case 2:
            printf("two\n");
            break;
    case 3:
            printf("three\n");
            break;
    default:
            printf("???\n");
            break:
}

///ELSE-IF///

if (echoNumber == 1)
{
    printf("one\n");
}
else if (echoNumber == 2)
{
    printf("two\n");
}
else if (echoNumber == 3)
{
    printf("three\n");
}
else
{
    printf("???\n");
}

```

2.easier to group multiple cases

```c
///switch///

switch (prinmeNumber)
{
    case1:
    case2:
    case3:
    case5:
            printf("prime\n");
            break;
    case4:
    case6:
            printf("not\n");
            break;
    default:
            printf("???\n");
            beak;
}

///ELSE-IF///

if (primeNumber == 1
    || primeNumber == 2
    || primeNumber == 3
    || primeNumber == 5)
{
    printf("prime\n");
}
else-if (primeNumber == 4
        || primeNumber == 6)
{
    printf("not\n");
}
else
{
    printf("???\n");
}

```

3.faster.../easier to optimize...

a switch generates a jump table in asssembly which is generally faster (depends on use case, compiler and underlying architecture)

4.ELSE-IF does not allow "fall through"

```c
///switch///

switch (countToNum)
{
    case 3:
            printf("three\n");
    case 2:
            printf("two\n");
    case 1:
            printf("one\n");
    case 0:
            printf("launch!\n");
break;

    default:
            printf("???\n");
            break;
}

///ELSE-IF///

if (countToNum == 3)
{
    print("three\n");
    print("two\n");
    print("one\n");
    print("launch!!!\n");
}
else if (countToNum == 2)
{
    print("two\n");
    print("one\n");
    print("launch!!!\n");
}
else if (countToNum == 1)
{
    print("one\n");
    print("launch!!!\n");
}
else if (countToNum == 0)
{
    print("launch!!!\n");
}
else
{
    print("???\n");
}

```

>when should I use ELSE-IF isntead of SWITCH?

1. large ranges of cases (switch does not translate well to large ranges)
```c
///IF-EELSE///

if (rngNum >= 1 && rngNum <= 20)
{
    printf(("%d\n"), rngNum); 
}
else
{
    printf("???\n");
}

///SWITCH///

switch (rngNum)
{
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
    case 6:
    case 7:
    case 8:
    (etc...etc...)
    case 18:
    case 19:
    case 20:
            printf("%d\n", rngNum);
            break;
    default:
            printf("???\n");
            break;
}

```

2. conditional expressions (switch only evaluates constants)
```c
///ELSE-IF///

int inputNumber = 0;
scanf("%d", &inputNumber);
printf("number is ");

if (inputNumber > 0)
{
    printf("positive\n");
}
else if (inputNumber < 0)
{
    printf("negative\n");
}
else
{
    printf("zero\n");
}

///SWITCH///
int inputNumber = 0;
scanf("%d", &inputNumber);
printf("Number is ");

switch (inputNumber)
{
    case > 0:
    etc...etc...
}
/*SWITCH will result in a compiling error!*/
```
3. variable values (switch case values must be literals)
```c
///IF-ELSE///

char char1, char2;
scanf("%1c %1c", &char1, &char2);
printf("are they equal?\n");

if (char1 == char2)
{
    printf("yes\n");
}
else
{
    printf("no\n");
}

///SWITCH///

char char1, char2;
scanf("%1c %1c", &char1, &char2);
printf("are they equal?\n");

switch (char1)
{
    case char2:
    etc...etc...
}

/*SWITCH will result in a compiling error!*/
```
4. floating point values (floats are technically literals but DONT utilize == or switch with floats)
```c
///IF-ELSE///
float inputDecimal;
scanf("%f", &inputDecimal);
printf("equal to 3.14?\n");

if (inputDecimal > 3.14)
{
    printf("nope\n");
}
else if (inputDecimal < 3.14)
{
    printf("nope\n");
}
else
{
    printf("yes\n");
}

///SWITCH///
float inputDecimal;
scanf("%f", &inputDecimal);
printf("equal to 3.14?\n");

switch (inputDecimal)
{
    case 3.14:
    etc...etc...
}
/*SWITCH will result in a compiling error!*/
```
