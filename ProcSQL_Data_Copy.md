### PROC SQL - simple data copy 

** Macro structure**
 3 steps 

1 - data B; -> target 
2 - set A; -> input
3 - run;

```
data B;
	set A;
run;

```
** Proc SQL Structure **

3 steps

1 - proc sql
2 - create table B as -> target
2 - select * from A -> input
3 - quit

proc sql;
create table B as
select * from A;
quit;
```
MACRO | SQL |
------|------|

data B; | create table B; |

--------| --------

set A | select * from A |
run | quit |
