---  
share: "true"  
---  
# Grade Merger  
  
    
  
Author: Walter DeGering, Fall 2023  
  
    
  
The purpose of this project is to merge our grades from gh classroom to learningsuite.  
  
It accomplishes this in 2 steps,  
  
    
  
1. it downloads the grades from gh classroom  
  
2. it merges the LS grades from a csv into a final csv  
  
## Maintenance  
  
    
  
To update this always make changes from your personal github account. **Do not** make changes from the cs236 github account.  
  
    
  
When changes are made make sure to update this document.  
  
    
  
## Setup  
  
    
  
The only 2 things that should need to be done each semester are creating an access token AND updating the config file  
  
    
  
### Generate an Access Token  
  
    
  
Github Docs: [link](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)  
  
    
  
1. Go to github settings and select developer settings  
  
    
  
![](imgs/dev_settings.png)  
  
    
  
2. Select Tokens (classic)  
  
    
  
![](imgs/tokens.png)  
  
    
  
3. Select Generate Token  
  
    
  
![](imgs/generate_token.png)  
  
    
  
4. Give the token a description, a time limit and select the needed permissions.  
  
    
  
Best Practice suggests using the minimum needed permissions, and giving a finite time limit on the token. To the best of my knowladge the minimum permissions needed are:  
  
    
  
- repo  
  
- workflow  
  
- admin:org  
  
    
  
this may change so if you are geting a 404 error it may be related to your token permissions  
  
    
  
![](imgs/auth_token_settings.png)  
  
    
  
5. Copy the token into a file called token.txt  
  
    
  
This file is deliberatly included in the .gitignore to prevent it being uploaded to the repo. Be careful with how you keep, store and use this file  
  
    
  
### The Config File  
  
    
  
`Config.py` is designed to have all of the settings that may change. This includes such as early or late points, holidays, and project due dates. Below is an explanation of each part of `Config.py`.  
  
    
  
#### Timezone and Date Formats  
  
    
  
- **GITHUB_DATE_FORMAT**: The format used for GitHub submission timestamps. Currently set to "%Y-%m-%d %H:%M:%S %Z".  
  
    
  
- **MDT_TIMEZONE**: The timezone used for calculations. Currently set to Mountain Daylight Time (MDT). This timezone may be wrong, Utah now does not observe daylight savings. However, the library used does not yet support a dedicated Utah timezone.  
  
    
  
#### Early and Late Submission Configuration  
  
    
  
- **MAX_EARLY_DAYS**: Maximum number of days that can be earned for early submissions.  
  
    
  
- **MAX_LATE_DAYS**: Maximum number of days that can be earned for late submissions.  
  
    
  
- **POINTS_PER_DAY_EARLY**: Points earned per day for early submissions.  
  
    
  
- **POINTS_PER_DAY_LATE**: Points deducted per day for late submissions.  
  
    
  
- **COUNT_SATURDAY**, **COUNT_SUNDAY**: Set to `True` to count Saturday and Sunday as early or late days.  
  
    
  
- **COUNT_HOLIDAYS**: Set to `True` to count holidays as early or late days.  
  
    
  
- **HOLIDAYS**: A dictionary containing dates of holidays  
  
    
  
- **PROJECTS**: A dictionary with data about each project  
  
    
  
#### Locating the assignment id  
  
    
  
I used the github classroom cli to do this. Link to the command I used (the `assignment` command): [Here](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/using-github-classroom-with-github-cli#view-assignment-information)  
  
    
  
Github Classroom CLI Docs: [Here](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/using-github-classroom-with-github-cli)  
  
    
  
## Using the Script  
  
    
  
### Downloading Grades from Learning Suite  
  
    
  
1. Open the export tab, select all projects  
  
    
  
![](imgs/ls_grade_export.png)  
  
    
  
2. Use csv format and uncheck mark dropped scores  
  
    
  
![](imgs/Export_settings.png)  
  
    
  
3. I reccomend saving them as learningsuite.csv in your merge_grades folder  
  
    
  
Certainly! Here's an example for each argument:  
  
    
  
### Usage  
  
    
  
The script is designed to merge grades from Learning Suite and GitHub CSVs. Follow the instructions below to use the script effectively.  
  
    
  
I use primarily two commands:  
  
    
  
With downloading from github classroom  
  
    
  
```bash  
  
python main.py 012345 --download-scores  
  
```  
  
    
  
Without downloading from github classroom  
  
```bash  
  
python main.py 012345  
  
```  
  
    
  
#### Command-line Arguments  
  
    
  
- `--learningsuite-csv`: Path to the Learning Suite CSV file (default: "learningsuite.csv").  
  
    
  
  Example:  
  
  ```bash  
  
  python main.py 012345 --learningsuite-csv path/to/learningsuite.csv  
  
  ```  
  
    
  
- `--github-csv`: Path to the GitHub CSV file (default: "github.csv").  
  
    
  
  Example:  
  
  ```bash  
  
  python main.py 012345 --github-csv path/to/github.csv  
  
  ```  
  
    
  
- `--output-csv`: Path to the output merged CSV file (default: "UPLOAD_TO_LEARNING_SUITE.csv").  
  
    
  
  Example:  
  
  ```bash  
  
  python main.py 012345 --output-csv path/to/output.csv  
  
  ```  
  
    
  
- `--unlinked-gh-csv`: Path to the unlinked GitHub accounts CSV file (default: "unlinked_gh_accounts.csv").  
  
    
  
  Example:  
  
  ```bash  
  
  python main.py 012345 --unlinked-gh-csv path/to/unlinked_gh_accounts.csv  
  
  ```  
  
    
  
- `--errors-csv`: Path to the error log CSV file (default: "error_log.csv").  
  
    
  
  Example:  
  
  ```bash  
  
  python main.py 012345 --errors-csv path/to/error_log.csv  
  
  ```  
  
    
  
- `project_numbers`: List of project numbers to process. Provide one or more project numbers.  
  
    
  
  Examples:  
  
  ```bash  
  
  python main.py 123 # runs only 1, 2, and 3  
  
  python main.py 012345 # runs all 0-5  
  
  ```  
  
    
  
- `--download-scores`: Use this flag to download new scores from GitHub Classroom. This is false by default becuase you want to avoid uneccissary api calls.  
  
    
  
  Example:  
  
  ```bash  
  
  python main.py 012345 --download-scores  
  
  ```  
  
    
  
- `--verbose`: Use this flag to enable verbose mode. This will print extra information as the program runs  
  
    
  
  Example:  
  
  ```bash  
  
  --verbose  
  
  ```  
  
    
    
  
#### Output  
  
    
  
After running the script, the merged grades will be saved to the specified output CSV file. Additionally, unlinked GitHub accounts and errors will be logged to their respective CSV files if provided.  
  
    
  
Feel free to customize the file paths and options based on your specific use case.  
  
    
  
Make sure to have the required CSV files in the specified paths and provide the necessary project numbers for processing.  
  
    
  
### Common problems  
  
    
  
#### Student did not get expected grade  
  
    
  
The download feature on gh classroom pulls the most recent attempt, not the highest score one. This may result in some errors for students grades. These cases should be rare, so in these cases ask students to reach out if they have a problem, and if so just manually fix the grade  
  
    
  
#### Student does not show a grade at all  
  
    
  
The student must have a roster ID set. If that is set properly then make sure that the submission time was valid. If that is not the case check to make sure their most recent run was successful  
  
    
  
#### Invalid Submission Time  
  
    
  
Sometimes the actions do not properly log. In these cases fix the grades manually if a student reaches out to report an error.  
  
    
  
#### Python Dependencies  
  
    
  
You may need to download needed depandaincies. This should be fairly easy to do using pip.  
  
    
  
#### Student is given 40 out of 100  
  
    
  
This is a bug I wasn't able to fix elegantly. I added the following lines of code to the `GradeMerger.py`  
  
    
  
```python  
  
if (float(raw_score) == 40 and project_number not in [0, 1]):  
  
    raw_score = "100.0"  
  
```  
  
    
  
If this is fixed make sure to remove it. Keep this entry for the purpose of documentation.  
  
    
  
#### Error Code 500  
  
    
  
The `AssignmentDownloader` will try over and over again to download each file. If it fails it will sleep for 2 seconds. Each time it fails the amount of sleep will increase.  
  
    
  
Error code 500 is fairly common, especially with lots of submissions in an assignment.  
  
    
  
Github API Docs: [here](https://docs.github.com/en/rest/classroom/classroom?apiVersion=2022-11-28#get-assignment-grades)