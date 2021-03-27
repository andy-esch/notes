# `awk` tips and tricks

## Filter a large csv based on a column

```bash
awk -F ','  'BEGIN {OFS=","} { if ($5 == "Philadelphia")  print }' patterns-part4.csv >> philly-part1.csv
```
