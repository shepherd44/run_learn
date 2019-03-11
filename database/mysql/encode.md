# [mysql] encode

## hex

```sql
SELECT HEX(123);
SELECT HEX('123');
SELECT UNHEX('abc');
```

## base64

```sql
SELECT TO_BASE64(123);
SELECT TO_BASE64('123');
SELECT FROM_BASE64('MTIz=');
```