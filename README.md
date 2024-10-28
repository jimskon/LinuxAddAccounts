# LinuxAddAccounts
A script to add account using a CSV file of email addresses and passwords

## Usage
 1. Make the script executable:
```
chmod +x create_users.sh
```
 2. Run the script with the CSV file as an argument:
```
sudo ./create_users.sh users.csv
```
This script will read each email, create a username from the part before the "@", and set up the account with the provided password.






