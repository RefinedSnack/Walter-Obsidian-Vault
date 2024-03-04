---  
share: "true"  
---  
# ServerReadme  
  
BYU's pass-off driver for CS 236 projects, written in python.  
  
  
## Installation / Setup  
  
### 1. Setup script  
  
In order to install / set up the pass-off driver, run the following command:  
```shell  
./setup.sh  
```  
  
### 2. Configuration Writer  
  
A helper script to correctly create a configuration file.  
  
This is the command to call the configuration writer:  
```shell  
./write_config.sh  
```  
  
This script will check if `config.json` exists, and if so then load the existing values as defaults.  
  
At the end of the script, the new configuration will be printed for verification before saving to `config.json`.  
The user can also cancel at any time by sending a `KeyboardInterrupt` (typically done by pressing `CTRL+C`).  
  
If the user confirms the configuration, the new configuration data will be written to `config.json`,  
including overwriting any previous configuration data.  
  
**IMPORTANT**: if this script is called independently while the server is running, **THE SERVER MUST BE RESTARTED**  
for the changes to take effect.  
  
  
## Pass-off Driver  
  
The base process for running a single project submission through tests and recording its score.  
  
### Basic Usage  
  
This is the basic command to call the pass-off driver:  
```shell  
./passoff.sh net_id proj_number [--no-user-input]  
```  
  
In more detail, the following command-line arguments can be used:  
  
Required:  
1. `net_id`: The BYU Net ID of the student whose project is being submitted.  
2. `proj_number`: An integer from 1 to 5 indicating which project is being submitted.  
  
Optional:  
- `--no-user-input`: If present, all default choices will be made such that the user is never asked for input.  
    If omitted, the user may be asked for input.    
    This flag should always be used when this script is called by the submission website's back-end code.  
  
### Simultaneous pass-offs  
  
This version of the pass-off driver is designed to allow multiple simultaneous pass-offs to occur at once.  
  
Note that the pass-off is still only designed to run 1 pass-off at a time for any given Net ID.  
That is, Julia and Fred (two different students) could run their pass-offs at the same time even for the same project,  
but Julia could not run two different pass-offs (whether for the same project or different projects)  
at the same time under the same Net ID.  
  
A locking mechanism is in place to prevent such simultaneous pass-offs to occur.  
If a set of simultaneous pass-offs for the same Net ID somehow does occur,  
it may result in undefined or unexpected behavior.  
  
  
## Web Application  
  
A web application can be used by students to submit their code for pass-off,  
and to view the results of their previous submissions.  
  
### Dependencies  
  
The following external dependencies need to be installed or set up in order to run the web application server:  
  
- Redis: [installation instructions](https://redis.io/topics/quickstart)  
- Submission Passwords: see `auth/README.md` for more information.  
- Caddy: [installation instructions](https://caddyserver.com/docs/install#debian-ubuntu-raspbian)  
  
### Start the Server  
  
This is the command to start the server for the web application:  
```shell  
./start_server.sh port_num  
```  
  
Arguments:  
1. `port_num`: The port number for the server to be accessible from locally.  
  
Since the server is long-running, it should be detached from the current shell. To do so:  
1. Press `CTRL+Z` to pause the server process.  
2. Use the command `bg` to resume the process in the background.  
3. Use the command `disown` to detach the process from the current shell.  
  
This means you can close your shell and the server will continue to run.  
  
#### HTTPS Proxy  
  
It is also highly recommended that the server be run as an HTTPS server.  
This can easily be done using [caddy](https://caddyserver.com/).  
  
Follow these steps to use caddy as an HTTPS facade:  
1. Ensure port `80` and port `443` are both available. (Useful commands for this can be found in the  
    "Check on the Server" section of this document.)  
2. Use the command `caddy version` to check if caddy is installed. If you see a message such as  
    `bash: caddy: command not found`, that means it is not installed.  
3. To start caddy running an automatic HTTPS reverse proxy, use this command:    
    `sudo caddy reverse-proxy --from cs236.cs.byu.edu --to localhost:8080`    
    This assumes that the regular web application server is running on port `8080` and that the domain  
    name is `cs236.cs.byu.edu`. Either of these may be adjusted to your use case.  
  
The server can now be accessed securely at [https://cs236.cs.byu.edu](https://cs236.cs.byu.edu). Caddy  
will also automatically forward from [http://cs236.cs.byu.edu](http://cs236.cs.byu.edu) to the HTTPS URL.  
  
Once this caddy process is running, it also needs to be backgrounded and disowned for it to continue  
running when this shell is closed. Follow the three steps listed above to do to.  
  
### Stop the Server  
  
This is the command to stop the server for the web application:  
```shell  
./stop_server.sh  
```  
  
### Check on the Server  
  
Log files of all sorts are written in the `Log` directory. Files can be viewed from the command-line using  
tools such as `vim` or `less`.  
  
To view all processes on the serving machine, use the command `htop` to open a comprehensive view. This  
can also be used to manually terminate/interrupt processes. If a process to be terminated belongs to  
another user, you need to open htop as root using the command `sudo htop`.  
  
It's also helpful to be able to see which processes are attached to a certain port.  
Here are some example commands to check on port `8050`:  
- `sudo ss -lptn 'sport = :8050'`  
- `netcat -z localhost 8050`  
  
### Resetting for a new Semester  
  
At the end of a semester and the beginning of a new one, some grading information should be archived.  
Some information also needs to be cleaned out and reset.  
  
The following files/directories should be archived (save a backup copy in a separate location):  
- `auth/generated_passwords.csv`  
- `Key/`  
- `Log/`  
- `config.json`  
- `grades.db`  
  
The following files need to be deleted:  
- `auth/generated_passwords.csv` (new passwords should be generated for the new students and TAs)  
- the contents of `Log/` (leave the directory itself, but remove all of its contents)  
- `grades.db`  
  
Additionally, `config.json` needs to be updated for the new semester. This can be done by manually editing  
its contents, by running `./write_config.sh` to edit the contents, or by completely deleting the file and  
then running `./write_config.sh` to generate a new one from scratch.  
  
  
## Grades  
  
Grades are automatically recorded in a SQLite database named `grades.db`, both by manual  
TA-ran submissions, and by automated submissions run through the web app.  
  
### Upload Scores to BYU Learning Suite  
  
These grades will need to be periodically updated into BYU Learning Suite (LS).  
This repository contains a script `update_grades.sh` that can be used to compare scores  
between those recorded by the server (found in `grades.db`), and those found in LS.  
It assumes that grades saved in LS will only ever go up, and writes a new file that can  
be uploaded to LS to update all grades at once.  
  
To update grades from the pass-off driver into LS, follow these instructions:  
  
#### 1. Download LS Scores  
1. Open Learning Suite  
2. Navigate to the "BYU Grades" tab  
3. In the left panel, select "Import/Export"  
4. Again in the left panel, select the sub-section "Export"  
5. Select the check-marks for all the projects that the server is responsible for (typically 1 through 5)  
6. Ensure that the only other selected options are:  
    - "Net ID (Required)"  
    - "Points (Required)"  
    - "Comma-separated values (CSV) - Excel" (but not "Mark Dropped Scores")  
7. Click \[Export Scores\]  
  
#### 2. Move LS Scores  
1. Find the downloaded CSV file and ensure its format matches that of `grades_LS.csv`    
   (You can view the raw contents of the file using Notepad, vim, less, etc.)  
2. Copy the downloaded file onto the machine that has the pass-off driver  
3. Overwrite the contents of `grades_ls/grades_LS.csv` using the following command:    
`cat downloaded.csv > grades_ls/grades_LS.csv`    
  
#### 3. Run the Script  
Run the python script using the following command:    
`./update_grades.sh`  
  
You should then see this message as output:    
`please upload grades_ls/UPLOAD_TO_LS.csv to Learning Suite using the 'import' functionality`  
  
#### 4. Upload New Scores to LS  
The previous step created a file named `grades_ls/UPLOAD_TO_LS.csv`.  
This file contains the scores that need to be imported into LS.  
1. Copy `grades_ls/UPLOAD_TO_LS.csv` onto your local machine  
2. Open Learning Suite  
3. Navigate to the "BYU Grades" tab  
4. In the left panel, select "Import/Export"  
5. Again in the left panel, select the sub-section "Import"  
6. Upload `UPLOAD_TO_LS.csv` using the \[Choose Files\] button  
7. Ensure all displayed options are as expected  
8. Click \[Import\]  
9. Review the results, checking for errors like "ID not valid" that need to be resolved manually  
  
### Edit Due Dates and Other Config Variables  
  
If you'd like to change a project due date (or some of the other config variables) and have the  
recorded grades for already-submitted projects be retroactively adjusted, a script is provided  
to re-calculate grades with the newly changed config variable(s) taken into account.  
  
These are the config variables that can be changed even after projects have been submitted:  
- `free_attempts`  
- `cost_per_attempt`  
- `due_dates`  
- `absolute_due_date`  
- `holidays`  
- `count_weekends`  
- `count_holidays`  
- `off_days_counted_backward`  
- `early_days_max`  
- `early_bonus`  
- `late_days_max`  
- `after_max_late_gets_zero`  
- `late_penalty`  
  
The following config variables **CANNOT** be changed after projects have been submitted:  
- `n_projects`  
- `expressions`  
- `proj4_mega_test`  
- `timeout_seconds`  
- `valgrind_on`  
  
Note also that `expose_test_cases` *can* be changed after projects have been submitted,  
but it in no way has any bearing on how submissions are graded (rather, it only affects  
the student experience).  
  
It is "best practice" to only change variables in a way that could *increase* a student's score, and  
never *decrease* a student's score. For example, it is not "good practice" to move due dates to be  
*earlier* in time, but it is perfectly fine to move due dates to be *later* in time.  
  
To change one or more of the changeable config variables and then have grades re-calculated  
with the newly changed config variable(s) taken into account, follow these instructions:  
  
1. Edit the configuration.    
    This can be done by manually editing the `config.json` file, or using `write_config.sh`  
2. Stop the server.  
3. Run the grade-recalculating script.    
    This is done using the command `./recalculate_grades.sh`    
    The script will change the grades recorded in `grades.db` as needed, and report which students had scores that were changed.  
4. Start the server.  
  
The newly changed grades should be updated in BYU Learning Suite, also. This does not need to be done  
immediately and could be left to happen as part of the routine updating, or it could be done  
immediately after the 4 steps listed above.  
  
  
## Permissions  
  
In order to help assist with security, proper Unix file permissions should be maintained.  
  
#### Head TA  
  
The Head TA should have root access (`sudo` capabilities) on the machine where the web application server  
runs. Use this command to add a user to the `sudo` group, but replace `username` with the actual username:  
```shell  
usermod -aG sudo username  
```  
  
#### File Ownership  
  
For all files in this directory, the owning group should be the TA group `cs236ta`. If this is somehow  
not the case, use the `chown` command to change their owning group.  
It is also preferable that the owning user be the Head TA. This can be set also using the `chown` command.  
  
For help with using `chown`, see the short tutorial [here](https://linuxize.com/post/linux-chown-command/).  
  
#### Setting Permissions  
  
File permissions are set by the `set_permissions.sh` bash script, which is run automatically  
before the pass-off driver executes. However, if the script needs to be run manually, use this command:  
```shell  
./set_permissions.sh  
```  
  
You may need to first make the script executable using this command:  
```shell  
chmod ug+x set_permissions.sh  
```  
  
#### The Key Directory  
  
Since the `Key` directory is to be kept in read-only mode (as a safeguard to prevent student code from  
editing the input or output files), these files cannot be deliberately edited without special treatment,  
including any changes that may be applied by `git`. If these files do need to be edited, use this  
command to add write permissions:  
```shell  
chmod -R 770 Key  
```  
  
After your edits are complete, you should return the permissions to how they were before. This can  
easily be done with the `set_permissions.sh` bash script, described above.  
