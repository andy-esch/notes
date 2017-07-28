# pip

## List outdated packages

```bash
pip list --outdated --format=freeze
```

Upgrade all outdated packages

```bash
pip install --upgrade $(pip list --outdated --format=freeze | awk -F'==' '{ print $1 }' | tr '\n' ' ')
```
