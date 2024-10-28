#!/bin/bash

# Check for root privileges
if [ "$EUID" -ne 0 ]; then
  echo "Please run as root."
  exit 1
fi

# Check if a filename is provided
if [ -z "$1" ]; then
  echo "Usage: $0 users.csv"
  exit 1
fi

CSV_FILE="$1"

# Read CSV file and create users
while IFS=, read -r email password; do
  # Skip header or empty lines
  if [[ "$email" == "email" || -z "$email" || -z "$password" ]]; then
    continue
  fi

  # Extract username from the email
  username="${email%@*}"

  # Check if user already exists
  if id "$username" &>/dev/null; then
    echo "User $username already exists. Skipping..."
  else
    # Create the user and set password
    useradd -m "$username"
    echo "$username:$password" | chpasswd
    echo "Created user $username."
  fi
done < "$CSV_FILE"
