# Manual SQLi
## Identifying SQLi via Error Based Payloads
Try injecting characters that are reserved for databases in an attempt to produce an error.
Characters such as `'`, `\`, `--`, `/`, `.` are usually reserved.

If no errors are produced, send valid data, "true" injections ("or 1=1") and "false" injections ("and 1=0"). Then observe the difference, if any, between the outputs for the three data types.

>[!tip]+
> If "true" injections give feedback it might be worth using it to pull info off the DB.
> Commands such as
>```
' or 1=1 in (select @@version) -- //
>```
>Or
>```
' OR 1=1 in (SELECT * FROM users) -- //
>```
>Just might give you DB information inside error messages.
## UNION Based Payloads
The [_UNION_](https://www.w3schools.com/sql/sql_union.asp) keyword aids exploitation because it enables the execution of an extra SELECT statement and provides the results in the same query, thus concatenating two queries into one statement.

For **UNION** SQLi attacks to work, we first need to satisfy two conditions:

1. The injected **UNION** query has to include the same number of columns as the original query.
2. The data types need to be compatible between each column.

>[!todo]
>Please fill out the rest of the UNION based attack payload section
## Blind SQL Injection
>[!todo]
>Please do this one day Pascal

# Automatic SQLi
Automated SQLi can be very powerful, especially for quick checks. But it can often miss A LOT of stuff. Take everything from automated tools with a grain of salt, and never assume just because the tool couldn't do it that it's impossible.

Here's a list of known tools used for SQLi
Tools:
1. [[sqlmap]]
