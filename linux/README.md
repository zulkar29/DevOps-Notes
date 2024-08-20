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
Commands for managing file and directory permissions.
| Command | Description |
| --- | --- |
| chmod | Change Mode - modify file permissions |
| chown | Change Owner - modify file ownership |
| chgrp | Change Group - modify group ownership |


---

