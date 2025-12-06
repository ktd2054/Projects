# Linux CLI - Shells Bells

Explore the Linux command-line interface and use it to unveil Christmas mysteries.

## Working With CLI

Let's get started...

- echo "Hello World!" ---> run first command to print a text
- ls -----> to list the contents
- cat ____.txt  -----> to read the file
- pwd ----> working directory
- cd  ------> change directory

### Looking for hidden file 

To find hidden files we must use _ls -la_ command where l shows file permissions and owner and -a shows the hidden files.

- these files or directory can be hidden by using dot(.) symbol at starting of the name of the document.

### Grepping the logs

- different log files stores distinct logs from the OS and system.

_grep_ command is used to look for specific text inside a file. e.g . _grep "Failed password" auth.log_

### Finding the files

to find a file we can use _find_ command. eg. find /directories/ -name *a word to search*


### .sh files

they contains CLI commands and are known as shell scripts.


### More Notes 

- # --> is comment 
- sort ----> for sorting
- uniq ----> lists unique items
- rm -----> deletes a file
- mv file1 file2 ----> moves ccontents inside from file1 to files 2


### CLI features

- | -------> sends the output from first command before the symbol to next after the symbol .. eg.. cat one.txt sort | uniq
- > or  >> -------> overwrite or append the file 
- && -------> runs the 2nd command if the first was successful 

### System Utilities


- uptime -------> to see how long a system is running
- ip addr ------->  check IP address
- ps aux -------> list all the process
- sudo su -------> switch root
- whoami -------> check the current user
- cat .bash_history -------> history of commands





