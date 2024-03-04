---  
share: "true"  
---  
# DREAD  
  
### Damage  
- How bad would an attack be  
### Reproducibility  
- how easy is this to reproduce or test  
### Exploitability  
- How much work does it take to launch an attack  
### Affected Users  
- How many people will be impacted  
### Discoverability  
- How easy is it to discover an attack  
  
Example payroll application, malicious user views confidential on-the-wire payroll data  
0-3 scale  
  
| Factor | Score | Reason                                   |  
|--------|-------|------------------------------------------|  
| D      | 3     | Payroll data is extremely sensitive      |  
| R      | 3     | 100% reproducible                        |  
| E      | 2     | Must be on the application’s subnet      |  
| A      | 3     | Affects everyone                         |  
| D      | 3     | Easy for attacker to identify vulnerability |  
  
Total: 14 (very bad)  
How bad is it?  
  
- 5 - 7: low risk  
- 8 - 11: medium risk  
- 12 - 15: high risk  
  
Lots of criticism, because scores can be subjective and can vary based on individual perspectives.  
  
  
Fill out a DREAD table with your neighbor and then discuss with the class:  
  
- Smart home  
    - You have a smart home system that can be unlocked by an app (e.g. you have a family member who forgot their key)  
    - There is a vulnerability in the smart home provider’s server that controls access to your home  
  
| Factor | Score | Reason                                   |  
|--------|-------|------------------------------------------|  
| D      | 3     | Access to your customers is very important      |  
| R      | 3     | Not sure here, not enough data                        |  
| E      | 2     | You have to know which users home is vulnerable      |  
| A      | 3     | Not sure here, not enough data                         |  
| D      | 2     | Not sure here, not enough data |  
  
  
- Bank website  
      
    - A customer’s password is easy to guess  
  
| Factor | Score | Reason                                   |  
|--------|-------|------------------------------------------|  
| D      | 3     | Banking data is very sensitive      |  
| R      | 3     | 100% reproducible                        |  
| E      | 2     | Must be on the application’s subnet      |  
| A      | 1     | Affects just users with bad passwords                         |  
| D      | 1     | Attacker needs to get ahold of username information an try lots of passwords |  
