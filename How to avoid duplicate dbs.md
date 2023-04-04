---
```smalltalk
Metacello new
                baseline: 'RdvNote';
                repository: 'gitlocal:///C:\devzone\sources\note_gtoolkit\src';
                load.
    (LeDatabasesRegistry defaultLogicalDatabase properties)
        addRegisteredDirectory: (FileReference fileSystem: FileSystem disk path: (Path from: 'C:\devzone\sources\note_gtoolkit\lepiter')).
    LeDatabasesRegistry default defaultLogicalDatabase reload.
````
Everything is fine when I start with a fresh downloaded version of GToolkit. However, If I restart it, I get the message: *"Error: Duplicate Registered Database: C:\devzone\sources\note_gtoolkit\lepiter*, and things can become weird in this lepiter database after. 
Is there a better way to automatically add a local project with its lepiter database on GToolkit startup ? Or how can I avoid the duplicate effect ?

ANSWER

This is the script I run between multiple project loads to prevent similar problems:
```smalltalk
dld := LeDatabasesRegistry defaultLogicalDatabase.
dld primaryDB: dld playgroundDB.
dld registeredDBs do: [ :e | dld removeDB: e ].
```