# BASH SCRIPTING

* `echo <message>` prints <message> in the terminal
* `<filename>.sh` shell script or sh-file
* `sh <filename>.sh` running a sh file using the `shell` interpreter.
* `bash <filename>.sh` running a sh file using the `bash` interpreter.
* `which bash` where the bash interpreter is located.
* `#!<path to interpreter>` tells the program to use the interpreter in a specific path. If you place this command in your script, you will be able to run the script with just `./<filename>.sh`
* `chmod +x <filename>.sh` give everyone executable permission
* `VARIABLE=VALUE` create a variable, there can be no spaces in between
* `$VARIABLE` to use a variable
* `read VARIABLE` read user's inputs and store it in a variable. note, you don't need `$` infront of a variable, when reading a user input.
* `man <command>` see the manual of a command
* `./<filename>.sh arg1 arg2 arg3` you can pass arguments when running the script, can check with `echo $*` to see all the arguments. `$1` for first argument and so on.
* if statement
  ```bash
  if [[ CONDITION ]]
  then
    STATEMENTS
  fi
  ```
* if else statement
  ```bash
  if [[ CONDITION ]]
  then
    STATEMENTS
  else
    STATEMENTS
  fi
  ```
* else if statement
  ```bash
  if (( CONDITION ))
  then
    STATEMENTS
  elif [[ CONDITION ]]
  then
    STATEMENTS
  fi
  ```
* `-eq` equal
* `-ne` not equal
* `-le` less than or equal
* `-ge` greater than or equal
* `-gt` greater than
* `-lt` less than
* you can type the expression in the terminal like `[[ 4 -lt 5 ]]` then find out the out put with `echo $?`
* or you can use one liner `[[ 4 -lt 5 ]]; echo $?`
* `&&` and operator
* `||` or operator
* for loop
  ```bash
  for (( i = 10; i > 0; i-- ))
  do
    echo $i
  done
  ```
* while loop
  ```bash
  while [[ CONDITION ]]
  do
    STATEMENTS
  done
  ```
  Example:
  ```bash
  while [[ $I -ge 0 ]]
  do
    echo $I
    (( I-- ))
    sleep 1
  done
  ```
* until loop
  ```bash
  until [[ CONDITION ]]
  do
    STATEMENTS
  done
  ```
* `sleep(1)` pause execution for 1 second
* `:'multiline comment can come here'` multi line comment
* `printenv` command prints env variables
* `declare -p` view all variables in the shell
* `echo $RANDOM` generate a random number
* `I=$(( J + 1 ))` assign an expression to a variable
* `ARR=("a" "b" "c")` declare a variable
* `echo ${ARR[1]}` accessing values in an array
* `${#ARR[@]}` length of an arry
* function
  ```bash
  FUNCTION_NAME() {
    STATEMENTS
  }
  ```
* `=~` perfomrs reguar expression match
