# Common Linux Commands

## File and Directory Management

```bash
ls        # List directory contents
cd        # Change directory
pwd       # Show current directory
mkdir     # Create new directory
rmdir     # Remove empty directory
rm        # Remove files or directories
cp        # Copy files or directories
mv        # Move/rename files or directories
touch     # Create empty file
find      # Search for files
stat      # Display detailed info about a file
```

## File Viewing and Editing

```bash
cat       # View file contents
less      # View file contents one page at a time
more      # Similar to less
head      # View first lines of a file
tail      # View last lines of a file
tail -f   # Live monitor a file (e.g., logs)
nano      # Simple terminal-based text editor
```

## Searching and Text Processing

```bash
grep      # Search text using patterns
awk       # Pattern scanning and processing
sed       # Stream editor (e.g., find & replace)
sort      # Sort text lines
uniq      # Remove duplicate lines
cut       # Extract columns or fields
tr        # Translate or delete characters
wc        # Word, line, and character count
```

## Archiving and Compression

```bash
tar       # Archive files
gzip      # Compress files with gzip
gunzip    # Decompress .gz files
zip       # Compress files
unzip     # Extract .zip files
```

## System Information

```bash
top             # Real-time process monitor
htop            # Interactive process viewer
free -h         # Memory usage
df -h           # Disk usage
```

## Networking

```bash
curl <url>      # Fetch URL contents
wget <url>      # Download from URL
scp user@host:file .   # Secure copy
ssh user@host   # Secure shell login
```

## Miscellaneous

```bash
echo "text"      # Print text to terminal
date             # Show current date and time
cal              # Show calendar
history          # Command history
```

---

This list covers the most commonly used Linux commands for daily tasks. For further usage, use `man <command>` to view detailed manuals.
