###  MACRO proc;run;

** USUAL STRUCTURE**

Usual structures always starts with "PROC;" and ends with "RUN;"

	Proc is followed by the functions (sql, means, count, max, min, sum, etc) followed by the dataset;
		Followed by the variable, table, query, etc;
	Followed by "run";
	
The dataset is indicated by the libraryName.dataset

```
proc function data = library.dataset;2
var
run;
```
 
 **MACRO STRUCTURE**
 
 Get a long a complex code and simplify it by using parameters
 	Lets code more elegant, simpler and easier to read and to mantain.
 
 
 ```
 %macro
 
 %mend
 ```
 
 ```
%macro myreport(lib,dsn,statvar);
proc means data=&lib..&dsn;
var &statvar;
run;
proc print data=&lib..&dsn;
run;
%mend;

%myreport(sashelp,class,age);
%myreport(sashelp,cars,msrp);
 ```
*/


/*1 PROGRAM - PROC MEANS IN A **CLASSIC** STRUCTURE 6 * 3 = repeted code lines 18 in total*/ 
proc means data	= SASHELP.CLASS; /* proc + funcion + dataset   // the mean fuction returns the averages calculations for the variable age declared below*/
var age;
run;
proc means data	= SASHELP.AIRLINE; 
var air;
run;
proc means data	= SASHELP.STOCKS; 
var close;
run;
proc means data	= SASHELP.CARS; 
var weight;
run;
proc means data	= SASHELP.ELECTRIC; 
var revenue;
run;
proc means data	= SASHELP.GAS; 
var cpratio;
run;

/*1 PROGRAM - PROC MEANS IN **MACRO** STRUCTURE (5 macro lines of code + 1 line for each table >> 11 in total, and 2 less than usual query for each table)*/

%macro random_mean(library, dataset, mean_var); /* %macro  macro_name  (macro_variables,,,)*/
proc means data = &library..&dataset; /*it's necesary to use the & before each macro variable //macro variables separeted by 2 dots".."*/
var &mean_var;						  /*it's necesary to use the & before each macro variable*/
run;
%mend;								/*Macro's end with %mend*/

%random_mean(sashelp, class, age); /* %macro_name() calls the macro*/
%random_mean(sashelp, airline, air);
%random_mean(sashelp, stocks, close);
%random_mean(sashelp, cars, weight);
%random_mean(sashelp, electric, revenue);
%random_mean(sashelp, gas, cpratio);


/**********************************************************************************************************/

proc print data = sashelp.cars; /* Prints just de columns from dataset declared into var. Doesn't need comas beetwen the variables*/
run;

proc print data = sashelp.cars; /* Prints the entire dataset*/
var msrp type;
run;

proc print data = sashelp.class; 
run;

proc print data = sashelp.electric; 
run;

proc print data = sashelp.gas; 
run;

proc print data = sashelp.airline; 
run;

proc print data = sashelp.stocks; 
run;

/**********************************************************************************************************/
/*
### Positional Macro Parameters

If it's not declared the name of the macro definitions, to use the macro invoque it's necesary to keep the same order of the parameters
Also the number of parameters should match

```
%macro myreport(lib,dsn,statvar); // here insed the parentesis are the (macro definition)
proc means data=&lib..&dsn;
var &statvar;
run;
%myreport(sashelp,class,age); // here insed the parentesis are the (macro invoque)
```

### Keyword Macro Parameters

Alows to re-order the parameters, because they have a name
It's not necesary to march the number of parameters

```
%macro myreport(lib=,dsn=,statvar=); 
proc means data=&lib..&dsn;
var &statvar;
run;
proc print data=lib..dsn;
run;
%mend;

%myreport(lib=sashelp,statvar=age,dsn=class); // distinc order works and also missing parameters
```

```
%macro myreport(lib=,dsn=,statvar=); 
proc means data=&lib..&dsn;
var &statvar;
run;
proc print data=lib..dsn;
run;
%mend;

%myreport(lib=sashelp,dsn=class); // also missing parameters works >> returns the means for all variables // but the lib and dsn are mandatory 
```

*/

%macro myreport(lib=,dsn=,statvar=); 
proc means data=&lib..&dsn;
var &statvar;
run;
proc print data=&lib..&dsn;
run;
%mend;

%myreport(lib=sashelp,dsn=class); 

