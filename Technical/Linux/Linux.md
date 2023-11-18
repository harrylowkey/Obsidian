
### Local softwares:

1. Their bin files are located at
	- Binary files are located at: `/usr/local/bin/`
	- node_modules directory is located at: `/usr/local/lib/node_modules`
	- docker is located at: `/usr/local/lib/docker
-> They are the packages & application & softwares and their's binary files which we installed. Not the default linux ones. The linux ones are located at `/usr/bin`, `/usr/lib`

2. Their log files are located at:
	- `/usr/local/var`




## Commands

1. Get ex-commands:
    
    ```bash
    history
    ```
    
2. Add text to file using cat:
    
    ```bash
    cat 1|2 > output.txt
    ```
    
3. Search files: find:
    
    ```bash
    find ~/Dev/megatron/renyoo_api/ -iname src
    find location/ -type -name -size
    ```
    
4. Search text in file:
    
    ```bash
    grep -c -I “harry dang” text.txt
    ```
    
5. File Archiving and Compression:
    
    ```bash
    # Archiving
    tar -cvzf file-name files-to-gzip
    
    # Extract gzip file
    tar -xvzf file-name
    ```
    

**File system:**

![Untitled](File%20systems%20tree%202.webp)

![Untitled](File%20systems%20tree.png)