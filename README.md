# clear-breeze-server-level
Clear Breeze for all applications in a server

1. Connect to server via SSH (VSCODE)
2. Navigate to `cd applications`
3. Run the following commands `for A in $(ls -l /home/master/applications/| grep "^d" | awk '{print $NF}'); do echo "Application: $A"; cd /home/master/applications/$A/public_html/ && wp breeze purge --cache=all ; done`

Command above loops through all of the applications and then runs `wp breeze purge -cache=all` in each `/public_html/` folder.
