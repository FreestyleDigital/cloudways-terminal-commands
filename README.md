# Cloudways Terminal Commands
Useful bash scripts to use on a Cloudways server


# How to clear Breeze in all applications on a specific server
Clear Breeze for all applications on a server

1. Connect to server via SSH (VSCODE)
2. Navigate to `cd applications`
3. Run the following commands in the terminal `for A in $(ls -l /home/master/applications/| grep "^d" | awk '{print $NF}'); do echo "Application: $A"; cd /home/master/applications/$A/public_html/ && wp breeze purge --cache=all ; done`

Command above loops through all of the applications and then runs `wp breeze purge -cache=all` in each `/public_html/` folder.

&nbsp;
&nbsp;
&nbsp;

# How to check if a plugin is installed/not installed in all applications on a specific server
Check whether a plugin is installed in all applications on a server

1. Connect to server via SSH (VSCODE)
2. Navigate to `cd applications`
3. Run the following commands in the terminal 
4. `for A in $(ls -l /home/master/applications/| grep "^d" | awk '{print $NF}'); 
do
cd /home/master/applications/$A/public_html/ && 
if ! wp plugin is-installed cleantalk-spam-protect
then
  echo "Not Installed: $A";
fi;
done`

Command above loops through all of the applications and then runs `wp plugin is-installed (PLUGIN NAME)` in each `/public_html/` folder. An exclamation mark is used infront of the IF statement condition to check if NOT installed.
