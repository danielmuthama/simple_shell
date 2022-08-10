# <a href="url"><img src="https://images.assetsdelivery.com/compings_v2/dmstudio/dmstudio1606/dmstudio160600030.jpg" align="middle" width="100" height="100"></a> simple_shell

<a href="https://alxafrica.com"><img src="https://lh3.googleusercontent.com/oVJxT1yn7vwaEM8t9A5MGL6emG0j-_uqHa5H8ikWLvl6Ka-nVmUJZblqWDqPiY-S6itPLnZNgcc8rviK8AVT65l_a3zHiyctwy8=s0" align="right" width="200" height="200" alt="Alx School" border="0"></a>
A simple UNIX command interpreter that provides a user interface to access and give orders to the operating system.

## Table of Contents
* [Description](#description)
* [File Structure](#file-structure)
* [Requirements](#requirements)
* [Installation](#installation)
* [Usage](#usage)
* [Example of Use](#example-of-use)
* [Bugs](#bugs)
* [Authors](#authors)

## Description
This is a command line interpreter, or shell, in the tradition of the first Unix shell written by Ken Thompson in 1971. This was made as a project for Holberton School. In this project we apply the knowledge that we have learned in C programming language.
Standard functions and system calls employed in simple_shell include:
   ```sh
   access, execve, exit, fork, free, malloc, read, signal, wait, write.
   ```
   
## File Structure
* [AUTHORS](AUTHORS) - List of contributors to this repository
* [man_1_simple_shell](man_1_simple_shell) - Manual page for the simple_shell
* [shell.h](shell.h) - program header file
* [shell.c](simple_shell.c) - main function of the shell
  * `main` - the main function of the program
  * `ret` - return function
  * `extstatus` - return status
  * `writeexe` - writes to standar error
  * `writes0` - writes to standar error
 

## Requirements

simple_shell is designed to run in the `Ubuntu 20.04 LTS` linux environment and to be compiled using the GNU compiler collection v. `gcc 4.8.4` with flags`-Wall, -Werror, -Wextra, and -pedantic.`

## Installation

   - Clone this repository: `git clone "https://github.com/Timex19/simple_shell.git"`
   - Change directories into the repository: `cd simple_shell`
   - Compile: `gcc -Wall -Werror -Wextra -pedantic *.c -o hsh`
   - Run the shell in interactive mode: `./hsh`
   - Or run the shell in non-interactive mode: example `echo "pwd" | ./hsh`

## Usage

The simple_shell is designed to execute commands in a similar manner to sh, however with more limited functionality. The development of this shell is ongoing. The below features will be checked as they become available (see man page for complete information on usage):

### Features
- [x] uses the PATH
- [x] implements builtins
- [x] handles command line arguments
- [x] custom strtok function
- [x] uses exit status
- [x] shell continues upon Crtl+C (**^C**)
- [x] handles comments (#)
- [x] handles **;**
- [x] custom getline type function
- [ ] handles **&&** and **||**
- [ ] aliases
- [ ] variable replacement


### Built-ins

- [x] exit
- [x] env
- [ ] setenv
- [ ] unsetenv
- [x] cd
- [ ] help
- [ ] history

### Examples
<div id="examples"><div/>

1. Absolute path commands
- non interactive
```bash
$ echo "/bin/pwd" | ./hsh
$ /home/timex/simple_shell
```
- interactive mode
``` bash
$ ./hsh
./hsh$ /bin/echo hello world
helo world
./hsh$ exit
$
```
2. short command
- non interactive
```bash
$ echo "pwd" | ./hsh
$ /home/timex/simple_shell
```
- interactive mode
``` bash
$ ./hsh
./hsh$ echo hello world
helo world
./hsh$ exit
$
```
3. built-ins
- non interactive
```bash
$ echo "exit" | ./hsh
$ echo $?
0
```
- interactive mode
``` bash
$ ./hsh
./hsh$ exit 98
$ echo $?
98
```

**Some error output**
``` bash
$ ./hsh
./hsh$ ls /non_existing_folder
ls: cannot access '/non_existing_folder': No such file or directory
./hsh$ exit
$ echo $?
2
```
``` bash
$ echo "non_valid_command" | ./hsh
./hsh: 1: non_valid_command: not found
$ echo $?
127
```

## Project files
| File        | Description |
| ----------- | ----------- |
| `AUTHORS`     | File with names of the owners and authors of this project |
| `README.md`   | Nutshell description of simple_shell project |
| `aux_funs.c`  | Auxiliar functions <br> **signal_exit:** handler for SIGINT signals <br> **_calloc:** allocate memory and fills it with zeros
| `built-ins.`c | Built-ins functions: <br> **check_word:** evalute alpha chars in string <br> **exit_built_in:** stop execution of shell <br> **env_built_in:** prints environment variables |
| `core_funs.c` | Heart of simple_shell <br> **check_builtin:** check if first argument is a built-int <br> **not_found_error:** handler for print error when command is not found <br> **simple_exec:** decision flow for command execution|
| `path_funs.c` | Function to check command in path <br> **_getenv:** search variable in environment vars <br> **cmd_path:** concat first argument with PATH dirs |
| `shell.h`     | Header file <br> **All includes** <br> **All prototypes** <br> **Definition of struct params** |
| `simple_shell.c` | Initialize the simple_shell execution: <br> **test:** <br> Remove \n last char readed with getline <br> Tokenize and save in argv all arguments readed <br> Calls simple_exec <br> **main:** <br> Initialize params struct vars <br> Set signal listenes <br> Print prompt (interactive mode) <br> Read arguments with getline <br> Handle CTRL + D to stop execution|
| `string_funs.c`  | First string functions file <br> **_strcat:** concat string (no malloc) <br> **_strlen:** get length of string <br> **rev_string:** reverse a string <br> **_itoa:** convert int to string <br> **_strcmp:** compare two strings |
| `string_funs2.c`  | Second string functions file <br> **_strchr:** search char in string <br> **_strcpy:** copy string in other one <br> **str_concat:** concat string (malloc) <br> **_atoi:** convert string num, to int|


## Full documentation
For more info about this project you can run the man page:

`$ ./man_1_simple`

## Bugs
At this time, there are no known bugs.

## Authors

Ismaila Lawal Elijah [ElijahLawal-7](https://github.com/ElijahLawal-7) 

Juliet Owah [julietowah](https://github.com/julietowah)
