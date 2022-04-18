# Notes 

## `sed`

`-f` to specify the script file.
`-e` to pass edit command. If there is only one command, this flag is redudant.
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

```bash
awk '/MA/ { print $1 }' list
```

