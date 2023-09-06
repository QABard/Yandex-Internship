## PostgreSQL

### Task 1
  
The developers have assigned a task to determine which requests were sent from an IP address. 
I needed the addresses that start with "233.201.".
The logs were located on a remote server at the address logs/2019/12. The day when the error was occurred is unknown.
My task was to find out which requests were sent.

<br> The queries I used to get this logs:
<br> cd logs/2019/12 
grep -R "^233.201."
