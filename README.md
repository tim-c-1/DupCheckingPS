# DupCheckingPS
A Powershell solution for file preservation, duplicate checking, and hashing.

This script reads a given directory, gets the MD5 hash, compares that hash to an existing hash "rolodex", then copies non-duplicate files to the given destination.
It includes logging for runtimes for each script loop- allowing for tracking of script run times; uses robocopy to exclude duplicate files when copying and provide visual updates to the process progression.

# Use
- Running the script opens a dialogue which the user can input information for which directory should be hashed, and where it should go.

- Once finished, it asks the user if they would like to run through the script again to let the user keep the same session when performing data preservation.

## Setup
- Choose the location of the directory files by pasting the path in the set-location line.
- When first running the script, there will be no information in the "Hash directory" (the 'rolodex')- so it is recommended to first hash any existing files into this .csv file using the following code:
  
```
Get-ChildItem -path [insert target directory] -recurse | Get-FileHash -Algorithm MD5 | Export-Csv HashDir.csv
```
