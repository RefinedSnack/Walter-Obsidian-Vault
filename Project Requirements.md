---  
share: "true"  
---  
# Project Requirements  
  
Platform:  
- Ability to create an account  
- Login  
- Logout  
  
League Creation  
- The app should provide an option to create a new college fantasy football league.  
- The user should be able to specify the league name.  
- The user should be able to specify the draft date, and number of teams.  
- The user should be able to specify the number of teams.  
- The app should generate a unique league ID for each created league.  
- Once the league is created, the user should be able to invite friends to join using email addresses or a code.  
  
Snake Style Draft  
- The app should support a snake style draft. (rd 1 is 1-10 rd 2 is 10-1)  
- Users should be able to join the draft room at the specified draft date and time.  
- The draft order can be randomized or set by the league manager before the draft begins.  
- During the draft, users should have a timer for each pick (30-90 seconds), with the option to auto-draft if they don't pick in time.  
- Drafted players should be added to each team's roster automatically.  
  
Beyond the Scope of this project:  
- Team Management  
- Schedules  
- Scoring Calculations  
- Security  
	- Password managment  
	- Forgot Password  
	- Data encrypting  
- External API  
	- Ability to grab data from a source, for now we will 'mock' this in the project