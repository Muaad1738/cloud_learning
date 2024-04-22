# Basic Commands

## Uname
- `uname --help`: Displays help information about the uname command.
- `uname -a`: Prints all system information.

## Whoami
- `whoami`: Prints the username associated with the current effective user ID.

## Cat /etc/shells
- `cat /etc/shells`: Displays the list of valid login shells defined in the system.

## Ps
- `ps -p $$`: Displays information about the current process (the shell session).

## History
- `history`: Lists previously executed commands.

## Ls
- `ls -a`: Lists all files, including hidden ones.

## Curl
- `curl url -f --output file`: Fetches a file from the specified URL and saves it to the specified file.

## File
- `file {filename}`: Checks the type of the specified file.

## Mv
- `mv`: Moves files or directories.

## Cp
- `cp`: Copies files or directories.

## Rm
- `rm -r`: Removes directories and their contents recursively.

## Mkdir
- `mkdir`: Creates directories.

## Touch
- `touch`: Creates empty files.

## Nano
- `nano`: A simple text editor.

## Text Manipulation

### head
- `head -n 2 {filename}`: Prints the first 2 lines of the specified file.

### tail
- `tail -n 2 {filename}`: Prints the last 2 lines of the specified file.

### cat
- `cat -n {filename}`: Numbers all output lines.

### grep
- `grep {word} {filename}`: Displays lines containing a specified word in the given file.

## System Administration

### Tree
- `tree`: Lists contents of directories in a tree-like format.

### Cd
- `cd /`: Changes to the root directory.

### Systemctl
- `systemctl nginx`: Manages the Nginx service.

### Nano .bashrc
- `nano .bashrc`: Opens the .bashrc file in the Nano editor.

### Sudo su cd
- `sudo su cd`: Switches to the superuser and changes directory.

### Echo
- `echo`: Prints text to the terminal.

### Root
- `root`: Refers to the root user.

### Export
- `export $`: Sets an environment variable.

### Cd ..
- `cd ..`: Changes to the parent directory.

### Print env
- `print env`: Prints environment variables.

### Nano provision.sh
- `nano provision.sh`: Opens the provision.sh file in the Nano editor.

### Source .bashrc
- `source .bashrc`: Reloads the .bashrc file.

### Chmod +x
- `chmod +x`: Changes file permissions to executable.

## Process Commands

### Ps aux
- `ps aux`: Displays information about all processes.

### Top
- `top`: Displays dynamic real-time information about running processes.

### Sleep &
- `sleep &`: Delays execution of a command.

### Jobs
- `jobs`: Lists jobs running in the background.

### Kill
- `kill`: Terminates processes.

### Kill -9
- `kill -9`: Forcefully terminates processes.
