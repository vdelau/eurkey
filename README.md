The [EurKEY keyboard layout](https://eurkey.steffen.bruentjen.eu/start.html)
source for the [Keyboard Layout Files Creator]( https://github.com/39aldo39/klfc) (KLFC)

Build with:

```
$ klfc eurkey.json altgr.json control.json deadkeys.json -o output
```

The layout is split into multiple files:
- `eurkey.json`, the main file, includes the None and Shift shift-states
- `altgr.json`, includes the AltGr and Shift-AltGr shift-states, except dead keys
- `control.json`, includes the Control shift-states, mostly for some control characters
- `deadkeys.json`, (Shift-)AltGr shift states for the dead keys and dead key key pairs


## Converting a MSKLC file to JSON

The [Microsoft Keyboard Layout Creator](https://www.microsoft.com/en-us/download/details.aspx?id=102134) (MSKLC) can export a keymap to a KLC file. KLFC currently not read such a file directly.

MSKLC was used to extract the information from an installed EurKEY layout. MSKLC exports to KLC files, which KLFC can work with.

To convert the KLC file from UCS2 (UTF-16) to UTF-8, you can use `iconv`. The additional `sed` command removes the Byte-Order-Mark.
```
iconv -f ucs2 -t utf8 eurkey.klc | sed '1s/^\xEF\xBB\xBF//' > eurkey.utf8.klc
```

KLFC can than convert the KLC file to a JSON file.
```
klfc --from-klc eurkey.utf8.klc --json eurkey.json
```

This JSON file has been split up by hand into the individual files to create a bit of logical separation.
