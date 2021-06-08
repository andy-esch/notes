# Bash things


## Find Text in File(s)

Tip from <https://stackoverflow.com/questions/16956810/how-do-i-find-all-files-containing-specific-text-on-linux/16957078#16957078>

```bash
$ grep -rnw '/path/to/somewhere/' -e 'pattern'
```

Or as

```bash
$ grep -rnw pattern /path/to/somewhere

```

## cat EOF

Stream multiple sources to a file until an EOF is encountered

https://stackoverflow.com/a/21549836/15540870
