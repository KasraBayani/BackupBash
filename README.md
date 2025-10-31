This version is untested on new Linux versions. Try at your own risk!

# BackupBash

BackupBash is a versatile backup and restore Bash script that supports both graphical (Zenity) and command-line interfaces. It offers features like compression, encryption, incremental backups, logging, and scheduling via cron.

## Features

- **Backup and Restore Modes**
- **Compression Methods:** none, gzip, bzip2, zip, tar
- **Encryption Methods:** AES-256-CBC, ChaCha20
- **Incremental Backups**
- **Detailed Logging**
- **Scheduling via Cron**
- **Self-installation to PATH**

## Installation

### Prerequisites

### Steps

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/MrDarkna/BackupBash.git
   cd BackupBash
   ```

2. **Make the Script Executable:**  
    ```bash
    chmod +x BackupBash
    ```

3. **Install BackupBash:**  
    Run the installation command to copy the script to `/usr/local/bin` for global access.  
    ```bash
    ./BackupBash install
    ```

    **What Happens During Installation:**  
    - **Automatic Copy to `/usr/local/bin`:** The script is copied to `/usr/local/bin/BackupBash`, which is included in your system's PATH.
    - **Sets Execute Permissions:** Ensures the script is executable.
    - **Verification:** Confirms successful installation by checking the path.

4. **Run BackupBash:**  
    After installation, you can run the script from anywhere using:  
    ```bash
    BackupBash
    ```

    This command automatically handles installation-related tasks and provides you with options to perform backups or restores.

## Usage

BackupBash can be operated in two modes: GUI and CLI. This guide focuses on CLI usage for automation and scripting purposes.

## CLI Mode

### Launching CLI Mode:
Use specific commands and options to perform backup or restore operations.

#### Backup Example

Perform a backup using the command-line interface with the following options:

 ```bash
BackupBash backup -s /path/to/source -d /path/to/destination -n my_backup -c gzip>
```

#### Backup Parameters:
- `backup`: Specifies the backup mode.
- `-s`: **Source Directory** – The directory you want to back up.
- `-d`: **Destination Directory** – Where the backup will be stored.
- `-n`: **Backup Name** – A name for your backup file.
- `-c`: **Compression Method** – Choose from none, gzip, bzip2, zip, tar.
- `-e`: **Encrypt Backup** – yes or no.
- `-m`: **Encryption Method** – Choose between AES-256-CBC and ChaCha20 (required if encryption is yes).
- `-k`: **Encryption Key** – A strong key (required if encryption is yes).
- `-i`: **Incremental Backup** – yes or no.

#### Restore Example:
Restore data from a backup using the command-line interface:

```bash
BackupBash restore -f /path/to/backup.tar.gz -r /path/to/restore/destination -k "YourStrongP@ssw0rd!"
```

### Restore Parameters
- `restore`: Specifies the restore mode.
- `-f`: **Backup File** – The backup file you wish to restore.
- `-r`: **Restore Destination Directory** – Where the backup will be restored.
- `-k`: **Encryption Key** – Required if the backup is encrypted.

---

## Automated Installation and Usage

BackupBash simplifies the installation and execution process:

### Install the Script Globally:
```bash
./BackupBash install
```

This command copies the script to `/usr/local/bin`, making it accessible system-wide as `BackupBash`.

### Run the Script Using the Global Command:
After installation, execute the script from any directory:
```bash
BackupBash
```

The script will automatically handle installation-related tasks and provide you with the necessary options to perform backups or restores.

## Scheduling Backups via Cron

Automate regular backups by the user-friendly graphical interface - done through cron jobs.

### Steps to Schedule a Backup

#### Run a Backup with Scheduling Option:
When performing a backup in CLI mode, you can schedule it by adding the `--schedule` flag followed by the desired frequency (`daily`, `weekly`, `monthly`).
```bash
BackupBash backup -s /path/to/source -d /path/to/destination -n my_backup -c gzip -e yes -m AES-256-CBC -k "YourStrongP@ssw0rd!" -i yes --schedule daily
```

#### Cron Job Entries:

Depending on the chosen frequency, BackupBash will set up the appropriate cron job:

- **Daily at 2 AM:**
    ```bash
    0 2 * * * BackupBash backup -s "/path/to/source" -d "/path/to/destination" -n "daily_backup" -c gzip -e yes -m AES-256-CBC -k "YourStrongP@ssw0rd!" -i yes
    ```

- **Weekly on Sunday at 2 AM:**
    ```bash
    0 2 * * 0 BackupBash backup -s "/path/to/source" -d "/path/to/destination" -n "weekly_backup" -c gzip -e yes -m AES-256-CBC -k "YourStrongP@ssw0rd!" -i yes
    ```

- **Monthly on the 1st at 2 AM:**
    ```bash
    0 2 1 * * BackupBash backup -s "/path/to/source" -d "/path/to/destination" -n "monthly_backup" -c gzip -e yes -m AES-256-CBC -k "YourStrongP@ssw0rd!" -i yes
    ```

## License

This project is licensed under the MIT License.

## Acknowledgements

Thank you for using BackupBash! For more scripts and updates, visit my GitHub repository.
```
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![GitHub stars](https://img.shields.io/github/stars/MrDarkna/BackupBash.svg?style=social&label=Star)
