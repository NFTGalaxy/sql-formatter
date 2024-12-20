# identifierCase (experimental)

Converts identifiers to upper- or lowercase. Only unquoted identifiers are converted.

This option doesn't yet support all types of identifiers:

- prefixed variables like `@my_var` are not converted.
- parameter placeholders like `:param` are not converted.

**NB!** The use of this option is generally not recommended,
because SQL Formatter leans on the side of detecting as few keywords as possible
(to avoid converting them to uppercase when `keywordCase: "upper"` is used),
which on the flip side means that everything else will be labeled as identifiers.

The only reasonable cases to use this option is when you want all your SQL to
be either in uppercase or lowercase. But if you only want keywords to be in
uppercase, only use the `keywordCase: "upper"` option.

## Options

- `"preserve"` (default) preserves the original case.
- `"upper"` converts to uppercase.
- `"lower"` converts to lowercase.

### preserve

```
select
  count(a.Column1),
  max(a.Column2 + a.Column3),
  a.Column4 AS myCol
from
  Table1 as a
where
  Column6
  and Column7
group by
  Column4
```

### upper

```
select
  count(A.COLUMN1),
  max(A.COLUMN2 + A.COLUMN3),
  A.COLUMN4 AS MYCOL
from
  TABLE1 as A
where
  COLUMN6
  and COLUMN7
group by
  COLUMN4
```

### lower

```
select
  count(a.column1),
  max(a.column2 + a.column3),
  a.column4 AS mycol
from
  table1 as a
where
  column6
  and column7
group by
  column4
```
