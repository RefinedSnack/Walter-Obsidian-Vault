---  
share: "true"  
---  
# Type System Example  
e ::= n  
	| x   
	| (+ e e)   
	| (\* e e)  
	| (if e e e)  
	| (e e)       
	| ($\lambda$  (x) e)  
    | (rec name (x : $\tau_0$) $\tau_1$ e )  
$\tau \space ::= num \space$  
$\space \space| \space \tau \rightarrow \tau$  
  
### Numbers  
$n : num$  
$\therefore \Gamma \vdash n : num$  
  
### Identifiers  
  
### Add and multiply  
1) $\Gamma \vdash e_0 : num$  
2) $\Gamma \vdash e_1 : num$  
$\therefore \Gamma \vdash (+ \space e_{0} \space e_{1}) : num$  
OR  
$\therefore \Gamma \vdash (* \space e_{0} \space e_{1}) : num$  
  
  
  
### If  
  
### Application  
$\Gamma \vdash : $  
### $\lambda$'s  
  
  
### Recursion  
$\Gamma [x \rightarrow \tau_x , f \rightarrow \tau_x \rightarrow \tau] \vdash \space e:\tau$  
$\therefore \Gamma \vdash (rec \space f (x : \tau_x ) \space \tau \space e): \tau_0 \rightarrow \tau_1$  
