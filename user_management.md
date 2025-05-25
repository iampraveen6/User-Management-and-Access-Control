1. Create User Accounts with Secure Passwords
sudo adduser Sarah
sudo adduser Mike
Set passwords manually: min 8 character with 1Lower, 1 Upper, 1 Special, 1 Number

2. Create Isolated Workspace Directories
# Create workspace directories
sudo mkdir -p /home/Sarah/workspace
sudo mkdir -p /home/Mike/workspace

3. Assign Ownership and Set Permissions
# Change ownership
sudo chown -R Sarah:Sarah /home/Sarah/workspace
sudo chown -R Mike:Mike /home/Mike/workspace
# Set permissions so only the user can access (700)
sudo chmod 700 /home/Sarah/workspace
sudo chmod 700 /home/Mike/workspace

4. Implement Password Expiry Policy (Every 30 Days)
Edit this file /etc/login.defs for default system policy
set below variables
PASS_MAX_DAYS   30
PASS_MIN_DAYS   1
PASS_WARN_AGE   7

5. Enforce Password Complexity
Edit pam config
sudo nano /etc/pam.d/common-password
Add below values
password requisite pam_pwquality.so retry=3 minlen=8 ucredit=-1 lcredit=-1 dcredit=-1 ocredit=-1
