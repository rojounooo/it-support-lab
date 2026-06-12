# Skill: File and Folder Navigation Using the Command Line

---

## Accessing the Command Prompt

- Open the **Start Menu** and search for **cmd**
- Or run `Win + R` → type `cmd`

---

## Navigation and Directory Management

### `cd` — Change Directory

Navigate between directories.

```cmd
cd Documents                  # Move into a subdirectory
cd ..                         # Move up one level
cd \                          # Move to the root of the drive
cd C:\Users\Jane\Desktop      # Navigate to a full path
```

---

### `md` — Make Directory

Create a new folder.

```cmd
md Projects                   # Creates a folder named Projects in the current directory
md C:\Users\Jane\Projects     # Creates the folder at a specific path
```

---

### `rd` — Remove Directory

Delete a folder.

```cmd
rd Projects                   # Removes an empty folder
rd /s Projects                # Removes a folder and all its contents
rd /s /q Projects             # Removes without prompting for confirmation
```

> **Note:** `rd` will fail on a non-empty directory unless `/s` is used.

---

## Listing Directory Contents

### `dir` — List Files and Folders

```cmd
dir                           # Lists files and folders in the current directory
```

### Flags

| Flag | Effect |
|------|--------|
| `/p` | Pauses output after each full screen — useful in directories with many files |
| `/w` | Displays output in a wide format showing filenames only across multiple columns |
| `/a` | Shows all files including hidden and system files |

These can be combined:

```cmd
dir /p /w                     # Wide format with pagination
dir /a                        # Include hidden files
```

---

## Creating and Writing to Files

### `copy con` — Create a File

`copy con` reads input from the keyboard and writes it to a file. Press `Ctrl + Z` then `Enter` to save and exit.

```cmd
copy con notes.txt
This is the file content.
^Z
```

This creates `notes.txt` in the current directory with the typed content.

---

### Overwrite a File with `copy con`

Running `copy con` on an existing filename will overwrite it entirely.

```cmd
copy con notes.txt
This replaces the previous content.
^Z
```

> **Note:** There is no append mode with `copy con` — it always overwrites. To append to a file from the command line use `>>` redirection instead: `echo New line >> notes.txt`

---

## Wildcards

Wildcards allow commands to match multiple files by pattern.

| Wildcard | Matches |
|----------|---------|
| `*` | Any number of characters |
| `?` | Exactly one character |

### Examples

```cmd
dir *.txt                     # Lists all .txt files in the current directory
dir report?.txt               # Matches report1.txt, reportA.txt but not report10.txt
copy *.txt C:\Backup          # Copies all .txt files to C:\Backup
del temp*                     # Deletes all files starting with "temp"
```

> **Note:** Use `del` with wildcards carefully — there is no recycle bin for command line deletions.

> **Note:** No ticket for this as it was just an overview.