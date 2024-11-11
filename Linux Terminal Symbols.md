---
version:
  - v0.1gpt
---
# Linux Terminal Symbols

Sure, here’s a concise overview of each redirection symbol:

1. **`<`**: Redirects input from a file to a command. Example: `command < file.txt`
2. **`<<`**: "Here Document" for multi-line input in a script. Example: `command << EOF`
3. **`<<<`**: "Here String" for single-line input. Example: `command <<< "input string"`
4. **`>`**: Redirects output to a file, overwriting it. Example: `command > output.txt`
5. **`>>`**: Redirects output to a file, appending to it. Example: `command >> output.txt`
6. **`2>`**: Redirects error output to a file. Example: `command 2> error.txt`
7. **`2>>`**: Appends error output to a file. Example: `command 2>> error.txt`
8. **`&>`**: Redirects both output and error to a file. Example: `command &> output.txt`
9. **`2>&1`**: Redirects error output to standard output. Example: `command > output.txt 2>&1`
10. **`|`**: Pipes output of one command as input to another. Example: `command1 | command2`
11. **`>&`**: Redirects both output and error together. Example: `command >& output.txt`

This shortened list gives you a quick reference to understand and use each redirection symbol at a glance.
