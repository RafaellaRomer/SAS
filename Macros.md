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

### NESTED MACROS VARS

```
%let b=10;

%let a=b;

%put ---> &b;
%put ---> &a;
%put ---> &&a;
%put ---> &&&a;
```
