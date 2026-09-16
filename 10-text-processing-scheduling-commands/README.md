# 🔹 Text Processing & Scheduling Commands

Practical Linux command notes with screenshots. Replace the placeholder images in the `images/` folder with your own terminal screenshots.

## `cat notes.txt`

Display file contents.

```bash
cat notes.txt
```

![cat screenshot](images/cat.png)

## `less notes.txt`

View text page by page.

```bash
less notes.txt
```

![less screenshot](images/less.png)

## `head notes.txt`

Show the beginning of a file.

```bash
head notes.txt
```

![head screenshot](images/head.png)

## `tail notes.txt`

Show the end of a file.

```bash
tail notes.txt
```

![tail screenshot](images/tail.png)

## `grep "error" application.log`

Search text for a pattern.

```bash
grep "error" application.log
```

![grep screenshot](images/grep.png)

## `grep -r "TODO" .`

Search recursively in directories.

```bash
grep -r "TODO" .
```

![grep-r screenshot](images/grep-r.png)

## `find . -name "*.log"`

Find files/directories by conditions.

```bash
find . -name "*.log"
```

![find screenshot](images/find.png)

## `wc -l notes.txt`

Count lines, words, or bytes.

```bash
wc -l notes.txt
```

![wc screenshot](images/wc.png)

## `sort names.txt`

Sort lines of text.

```bash
sort names.txt
```

![sort screenshot](images/sort.png)

## `uniq names.txt`

Remove adjacent duplicate lines.

```bash
uniq names.txt
```

![uniq screenshot](images/uniq.png)

## `cut -d ',' -f 1 users.csv`

Extract sections/columns from lines.

```bash
cut -d ',' -f 1 users.csv
```

![cut screenshot](images/cut.png)

## `sed 's/Linux/linux/g' notes.txt`

Transform or replace text.

```bash
sed 's/Linux/linux/g' notes.txt
```

![sed screenshot](images/sed.png)

## `awk '{print $1}' names.txt`

Process structured text.

```bash
awk '{print $1}' names.txt
```

![awk screenshot](images/awk.png)

## `tr 'a-z' 'A-Z'`

Translate or delete characters.

```bash
tr 'a-z' 'A-Z'
```

![tr screenshot](images/tr.png)

## `ls -la | tee files.txt`

Write output to a file and terminal.

```bash
ls -la | tee files.txt
```

![tee screenshot](images/tee.png)

## `crontab -e`

Schedule recurring commands.

```bash
crontab -e
```

![crontab screenshot](images/crontab.png)

## `at 10:00`

Schedule a one-time command (if installed).

```bash
at 10:00
```

![at screenshot](images/at.png)
