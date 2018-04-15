# bash-tools

A collection of "utility" bash scripts.

### [bashlogging](https://github.com/stuart-knock/bash-tools/blob/master/bashlogging)
Defines several functions for fine grained control of logging information.
Writes different types of messages based on `LOGLEVEL`. The messages are
sent to either stdout, stderr, file, or both based on the `LOGTYPE` parameter.
The file output is prepended with date & time -- stdout/stderr aren't, however,
they do use coloured versions of the ERROR:, WARNING:, INFO:, and DEBUG: tags.

### [bashcheck](https://github.com/stuart-knock/bash-tools/blob/master/bashcheck)
Does a quick and dirty check of a bash script printing any potentially major
problems to stdout, specifically it checks for:
  + Assigning values to system variables in an unconstrained way, ie a way
    that will have side effects on the callers environment.
  + Assigning variables or defining functions using Built-in function names
    or keywords.

### [checkurl](https://github.com/stuart-knock/bash-tools/blob/master/checkurl)
Check if a web page is accessible. Useful as a utility function for
identifying dead links. Exit status is 0 if the web page is accessible.
If the page is inaccessible the script prints a warning message before
exiting with status 1.

### [checkPyImport](https://github.com/stuart-knock/bash-tools/blob/master/checkPyImport)
Starts python and imports the requested package before exiting.
A message is printed to standard out and the exit code is set 
based on success or failure of the import.

### [git-import-file](https://github.com/stuart-knock/bash-tools/blob/master/git-import-file)
Imports a single file from a source repository into a target repository,
including its complete commit history. There are a few conditions that
must be met for this to work, for example:
  + the source and target repositories must be in clean state;
  + the `target-file` must not exist.
  + any commits renaming `source-file` must not have modified its contents.
  + `git log --follow` must be able to trace `source-file`'s commit history
    back to the original commit.
