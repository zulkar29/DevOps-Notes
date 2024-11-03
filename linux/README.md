# Linux Cheat Sheet

## Table of Contents

- [File Operations](#file-operations)   
- [Directory Operations](#directory-operations)  
- [Process Management](#process-management)  
- [Networking](#networking)  
- [Disk Usage](#disk-usage)  
- [Ownership & Permissions](#ownership--permissions) 

## File operations
Common commands for working with files.
| Command | Description |
| --- | --- |
| ls | List all files and directories in the current directory |
| touch `filename` |  Create a file |
| cat `filename` | View contents of a file |
| less `filename` | View contents of a file with pagination |
| cp `filename1` `filename2` | Copy a file from filename1 to filename2 |
| mv `filename` `directory-path`/ | Move a file to a different directory |
| rm `filename` | Delete a file |

## Directory Operations
Common commands for navigating and manipulating the file system/directories.
| Command | Description |
| --- | --- |
| pwd | Print Working Directory |
| cd `directory-path` | Change Directory |
| mkdir `directory-name` | Make Directory |
| rmdir `directory-name` | Remove Directory |

## Process Management
Tools for managing active processes.
| Command | Description |
| --- | --- |
| top | Monitor system, process, and user information |
| ps | Snapshot of current processes |
| kill `pid` | Kill a process by ID |
| killall `processname` | Kill a process by name | 

## Networking
Commands for network operations.
| Command | Description |
| --- | --- |
| ifconfig | Display network configuration akin to ipconfig on Windows |
| ssh `user@hostname` | Secure Shell Login |
| scp `sourceFile` `user@hostname:destination` | Secure Copy |
| sftp `user@hostname` | Secure File Transfer Protocol |

## Disk Usage
Commands for analyzing and managing disk space.
| Command | Description |
| --- | --- |
| df | Display Filesystem Disk Space Usage |
| du | Estimate File & Directory Space Usage |
| fdisk | Disk Partition Manipulation |


## Ownership & Permissions

### Basic Permission Commands
| Command | Description | Example |
| --- | --- | --- |
| chmod | Change Mode - modify file permissions | `chmod 755 file.txt` |
| chown | Change Owner - modify file ownership | `chown user:group file.txt` |
| chgrp | Change Group - modify group ownership | `chgrp dbadmin file.txt` |
| ls -l | List files with permission details | `ls -l /var/lib/mysql/` |
| stat | Display file status and permissions | `stat file.txt` |
| umask | Set default permissions for new files | `umask 022` |
| getfacl | Display file ACL permissions | `getfacl file.txt` |
| setfacl | Modify file ACL permissions | `setfacl -m u:user:rx file.txt` |

### Understanding Permission Notation

#### Symbolic Notation (Letters)
| Symbol | Category | Permission |
| --- | --- | --- |
| r | Read | View file contents or list directory contents |
| w | Write | Modify file or create/delete files in directory |
| x | Execute | Execute file or access directory |
| - | None | No permission granted |

#### Numeric Notation (Octal)
| Number | Permission Combination | Symbolic Equivalent |
| --- | --- | --- |
| 0 | No Permission | --- |
| 1 | Execute Only | --x |
| 2 | Write Only | -w- |
| 3 | Write and Execute | -wx |
| 4 | Read Only | r-- |
| 5 | Read and Execute | r-x |
| 6 | Read and Write | rw- |
| 7 | Read, Write, and Execute | rwx |

### Common Permission Patterns
| Octal | Symbolic | Use Case |
| --- | --- | --- |
| 755 | rwxr-xr-x | Executable files, directories |
| 644 | rw-r--r-- | Regular files |
| 777 | rwxrwxrwx | Full access (use with caution) |
| 700 | rwx------ | Private files |
| 600 | rw------- | Sensitive config files |
| 440 | r--r----- | Read-only for user and group |

