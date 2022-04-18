# Notes 

## `sed`

`-f` to specify the script file.\
`-e` to pass edit command. If there is only one command, this flag is redudant.\
`-n` Suppress automatic output of input lines. Must specify `/p` for each instruction intended to produce output.

E.g.

```bash
sed -n -e 's/MA/Massachussetts/p' list
```
Substitutes occurrences of `MA` with `Massachussetts` and prints out the affected lines.


## `awk`


`awk` allows field reference. `$0` represents the whole line, whereas `$1`, `$2` etc refer to individual fields. E.g.

```bash
awk '{ print $1 }' list
```

Prints out

```
John
Alice
Orville
Terry
Eric
Hubert
Amy
```
---
```bash
awk '/MA/ { print $1 }' list
```
prints out the first field of the lines matching the `/MA/` pattern.
```
John
Eric
Sal
```
---
The `-F` option changes the field separator (comma in the example below). Therefore the fields in the line `John Daggett, 341 King Road, Plymouth MA` are no longer the individual words. `$1` -> `John Daggett`, `$2` -> ` 341 King Road`, `$3` -> ` Plymouth MA`.

```bash
awk -F, '/MA/ { print $1 }' list
```
Result:
```
John Daggett
Eric Adams
Sal Carpenter
```
---
## Using `sed` and `awk` together
```bash
sed -f nameState list | ./byState
```
Output:
```
 California
         Amy Wilde
 Massachussetts
         Eric Adams
         John Daggett
         Sal Carpenter
 Oklahoma
         Orville Thomas
 Pennsylvania
         Terry Kalkas
 Virginia
         Alice Ford
```