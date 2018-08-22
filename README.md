The [EurKEY keyboard layout](https://eurkey.steffen.bruentjen.eu/start.html) 
source for the [Keyboard Layout Files Creator]( https://github.com/39aldo39/klfc)

Build with:

```
$ klfc eurkey.json altgr.json control.json deadkeys.json -o output
```  

The layout is split into multiple files:
- `eurkey.json`, the main file, includes the None and Shift shift-states
- `altgr.json`, includes the AltGr and Shift-AltGr shift-states, except dead keys
- `control.json`, includes the Control shift-states, mostly for some control characters
- `deadkeys.json`, (Shift-)AltGr shift states for the dead keys and dead key key pairs 
