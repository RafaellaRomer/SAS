/*
MACRO FUNCTIONS 

CHAR-LIKE VALUES

- Upcase
- Lowcase
- Substr
- Lenght

NUM-LIKE VALUES

- Eval - for simply integer operations
- Sysevalf - for complex and not integer operations


FUNCTIONS IN DATA 

x = function (a)

'x' is the target var
'a' is the input data

MACRO VARIABLES

b = %function(a);

b = %function(&a); // when 'a' is a variable


'b' target var
'a' input data

*/

/* MACRO FUNCTIONS CHAR-LIKE VALUES*/

%let a = United States;

%let b = %upcase(&a);
%put ---->>>  &b;

%let c = %lowcase(&a);
%put ---->>>  &c;

%let d = %substr(&a,1,6);
%put ---->>>  &d;

%let e = %length(&a);
%put ---->>>  &e;


/* MACRO FUNCTIONS NUM-LIKE VALUES*/

%LET x=3;
%LET y = 5;

%let z = &x + &y;
%put ----> &z;

%let b = %eval(&x + &y);
%put -----> &b;

%LET x =3.2;
%LET y = 5.7;

%let b = %sysevalf (&x + &y);
%put -----> &b;
