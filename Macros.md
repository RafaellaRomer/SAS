### CREATE A VARIABLE - %LET

```m
%let a = 10;
```

### CALL THE VARIABLE

```m
%put &a
```

### JUST TO SEE BETTER ON LOG WINDOW:

```
%put ----- > &a;
```
<img width="142" height="81" alt="image" src="https://github.com/user-attachments/assets/2836206e-732f-4a7a-82ef-0e409b1d2749" />

<img width="200" height="188" alt="image" src="https://github.com/user-attachments/assets/1cb7f345-5563-44c8-bd8a-aa5f677fb2fb" />


### DATA CODE TO CRATE AND EXTRACT DATA
```
data class;

input name $ gender $ age courseno major $;
cards;
John M 48 101 STAT
Peter M 58 101 HIST
Liz F 25 201 STAT
Joe M 28 301 ENGG
;
run;


proc print data = class;
var name age major;
where gender = 'M';
run;
```

<img width="229" height="211" alt="image" src="https://github.com/user-attachments/assets/f98ddb60-d70e-44af-824b-c4b3384bc38d" />  <img width="286" height="158" alt="image" src="https://github.com/user-attachments/assets/6a7fb983-2645-4a49-9131-24a073fd9a86" />
<img width="443" height="195" alt="image" src="https://github.com/user-attachments/assets/c0a221d5-8af8-4cb2-b6d6-b106b9ecc8fe" />

### DECLARING A VARIABLE IN THE SAME CODE

 dont need to be 'eclosed'
 needs to be called by the &
to call the variavle IN a data query, has to be in a "doble quotes"

```
data class;

input name $ gender $ age courseno major $;
cards;
John M 48 101 STAT
Peter M 58 101 HIST
Liz F 25 201 STAT
Joe M 28 301 ENGG
;
run;

%let sex = M;

proc print data = class;
var name age major;
where gender = "&sex";
run;
```
<img width="223" height="202" alt="image" src="https://github.com/user-attachments/assets/9c2edd40-13c2-4314-b347-82a144e3e057" />  <img width="297" height="152" alt="image" src="https://github.com/user-attachments/assets/a71bfe52-2fd7-442b-aa59-990a6216c467" />

### CREATING 2 MACRO VARIABLE - ONE CALLING ANOTHER

  -- var = age
  -- value = 28

```
data class;

input name $ gender $ age courseno major $;
cards;
John M 48 101 STAT
Peter M 58 101 HIST
Liz F 25 201 STAT
Joe M 28 301 ENGG
;
run;

%let var = age;
%let value = 28;

proc print data = class;
var name age major;
where &var = &value;
run;
```
  <img width="242" height="214" alt="image" src="https://github.com/user-attachments/assets/03aabc2b-342b-4009-bd9b-2fe08fab5d14" />  <img width="279" height="141" alt="image" src="https://github.com/user-attachments/assets/8197e6d9-8579-4252-b6ca-184e10a8e95a" />



### NESTED MACROS VARS

```
%let b=10;

%let a=b;

%put ---> &b;
%put ---> &a;
%put ---> &&a;
%put ---> &&&a;
```
