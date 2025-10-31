### Nested variables with Ampersand (&)

#### Rules of "&" and resolution

  1. Nested variables are read from left to right
  2. All consesecutive doble &s are resolved into a single "&". Except the last one
  3. It keeps reading till all the &s are resolved
  4. 
```
%let b=10;
%let a= b;

%put ----> &&&a;
```
 **OUTPUT**
 
<img width="277" height="83" alt="image" src="https://github.com/user-attachments/assets/a5c3abe6-dc91-4aef-86a3-cfa7480f59c9" />

- OBS.: Not posible to make math calculations, as as a macro variable, everuthing is stored as a string:

```
%let d=10;
%let c= d + 10; 

%put ----> &&&c;
```

**OUTPUT**

<img width="289" height="94" alt="image" src="https://github.com/user-attachments/assets/739735a2-d795-4ad3-b77d-87fce4027e88" />

  <img width="188" height="152" alt="image" src="https://github.com/user-attachments/assets/1ff1c09c-4775-4517-bcb0-b87b7be5a0e0" />    <img width="292" height="169" alt="image" src="https://github.com/user-attachments/assets/9ebdbf9b-98ec-488b-a22c-7063a9c2aa2d" />


------------

**IMPORTANT**
Each pair of & is read as 1 & for the next level, so it will keep retriving pair by pair and combining, till achieve the last &variable, wich can be a & + variable declared.
In the end, to achieve a nested variable, is needed a triple &&&& + variable: 

<img width="513" height="249" alt="image" src="https://github.com/user-attachments/assets/e8fb482e-4ed4-4117-8308-85d30ebadd24" />


**EXEMPLE 1** instead to return a 10 value received by variable b, it will receive the "b" value as a string:

```

%let b=10;
%let a= b;

%put ----> &&a;

```
**OUTPUT**

<img width="169" height="119" alt="image" src="https://github.com/user-attachments/assets/6dbb71fc-e4bc-496f-89b1-aea7eb575e7c" />

**EXEMPLE 2** The && becomes a & and the &a variable = b, so t becomes a &b during the reading porcess:

<img width="513" height="249" alt="image" src="https://github.com/user-attachments/assets/86167922-8897-4525-bf4f-f9a5c1c8e6b2" />


```
%let b=10;
%let a= b;

%put ----> &&&a;

```

<img width="300" height="80" alt="image" src="https://github.com/user-attachments/assets/ab359783-de5c-4e27-b8ba-66416b8533a6" />

**OUTPUT**

<img width="134" height="134" alt="image" src="https://github.com/user-attachments/assets/7cd0d27f-6c4a-4116-9681-7607e3726175" />

### MULTIPLES NESTED VARIABLES

```
%let book = story;
%let story = funny;
%let funny = twist;
%let twist = climax;
%let climax= teste_rafa;
%let teste_rafa=2 ;

%put ------> &book;
%put ------> &&book;
%put ------> &&&book;
%put ------> &&&&book;
%put ------> &&&&&book;
%put ------> &&&&&&book;
%put ------> &&&&&&&book;
%put ------> &&&&&&&&book;
%put ------> &&&&&&&&&&&&&&&book;

```

EXPLANATIONN: 

%put ------> &book; 												                        >> STORY 1
%put ------> &&book; >> &book 										                  >> STORY 2
%put ------> &&&book; >> (& + &book)-> &story 						          >> FUNNY 3
%put ------> &&&&book; >> &&book >> &book 							            >> STORY 4
%put ------> &&&&&book; >> (&& + &book)-> &&story >> &story 	      >> FUNNY 5
%put ------> &&&&&&book; &&&book >> &&story >> &story 				      >> FUNNY 6
%put ------> &&&&&&&book; (&&& + &book)-> &&&story >> &funny 	      >> TWIST 7
%put ------> &&&&&&&&book; &&&&book >> &&book >> &book 				      >> STORY 8
%put ------> &&&&&&&&&&&&&&&book; (&&&&&&&(7) + &book) >> 7&funny	  >> CLIMAX 15


<img width="565" height="142" alt="image" src="https://github.com/user-attachments/assets/f96a8808-73b7-4bbf-afdc-03bebd09bc95" />
