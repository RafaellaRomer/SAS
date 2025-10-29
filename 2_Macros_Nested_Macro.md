### Nested variables 

#### Rules of "&" and resolution

```
%let b=10;
%let a= b;

%put ----> &&&a;
```
 **OUTPUT**
<img width="277" height="83" alt="image" src="https://github.com/user-attachments/assets/a5c3abe6-dc91-4aef-86a3-cfa7480f59c9" />

---

  1. Nested variables are read from left to right
  2. All consesecutive doble &s are resolved into a single "&". Except the last one
  3. It keeps reading till all the &s are resolved

- OBS.: Not posible to make math calculations, as as a macro variable, everuthing is stored as a string

---
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

The last &variable is to retrieve the value of the nested variable, otherwhise, if puts jus 2 &s, it will store the given value as a text.

For exemple, instead to return a 10 value received by variable b, it will receive the "b" value as a string:

```

%let b=10;
%let a= b;

%put ----> &&a;

```
**OUTPUT**
<img width="169" height="119" alt="image" src="https://github.com/user-attachments/assets/6dbb71fc-e4bc-496f-89b1-aea7eb575e7c" />


