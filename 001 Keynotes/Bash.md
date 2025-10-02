#coding #linux
- aka Bourne Again SHell, is a SHell replacement for the linux or macos terminal.
- 
### Notes
- `$SHELL` : returns the current shell (Eg: bash, zsh, fish, etc).
- Before running a shell script for the first time we have to give it permission to run as an executable, it is done by `chmod +x <filename>.sh` | [[Unix]]
- `$<args-no>` takes the positional argument when the script is run from the user, just like an input method. 
- `>` writes the left commands output to a file. `>>` appends the left commands output to the file right to it.
- `<` feed the output of the right file/command to the LHS. `<<` Can feed multiple lines to its LHS. `<<<` feeds in a "string" into the LHS command.
- `$?` : returns the exit code of the last run command.
- `${1,,}` is parameter expansion and helps ignore upper and lower cases.
- To access the full list in bash we use `${<list-name}[@]`.
- 