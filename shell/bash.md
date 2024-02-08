# BASH
 - The [Bourne Shell](https://en.wikipedia.org/wiki/Bourne_shell) (`SH`) is a shell command-line interpreter for computer operating systems developed by Stephen Bourne at Bell Labs in 1979.
 - The [Bourne Again Shell](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) (`BASH`) was later created by Brian Fox in 1989 for the GNU Project as an improvement to the original shell script.
 - Also known as the UNIX shell
 - Use this [cheat sheet](https://devhints.io/bash) as a guide to writing code in bash syntax.

## shebang
 - The shebang is first line of a script that tells our computer where to run the file.
```bash
#! /usr/bin/env bash
```

## Files
### ~/.bashrc
 - The `.bashrc` file is executed each time you open a new terminal window.

### ~/.alias
 - The alias can be used to create variables, aliases, and functions to use in the terminal.
 - This file must be source in the .bashrc file.

## General Examples
```bash
#!/usr/bin/env bash

name="Justin"
echo "Hello $name!"
```

### Variables
```bash
name="Justin"
echo $name      # Justin
echo "$name"    # Justin
echo "${name}!" # Justin!
```

### String quotes
```bash
name="Justin"
echo "Hi ${name}"  # Hi Justin
echo 'Hi $name'  # Hi $name
```

### Shell execution
```bash
echo "I'm in $(pwd)"
```

### Conditional execution
```bash
git commit && git push
git commit || echo "Commit failed"
```

### Conditions
```bash
[[ -z STRING ]]	        # Empty string
[[ -n STRING ]]	        # Not empty string
[[ STRING == STRING ]]	# Equal
[[ STRING != STRING ]]	# Not Equal
[[ NUM -eq NUM ]]	    # Equal
[[ NUM -ne NUM ]]	    # Not equal
[[ NUM -lt NUM ]]	    # Less than
[[ NUM -le NUM ]]	    # Less than or equal
[[ NUM -gt NUM ]]	    # Greater than
[[ NUM -ge NUM ]]	    # Greater than or equal
[[ STRING =~ STRING ]]	# Regexp
(( NUM < NUM ))	        # Numeric conditions
[[ -o noclobber ]]	    # If OPTIONNAME is enabled
[[ ! EXPR ]]	        # Not
[[ X && Y ]]	        # And
[[ X || Y ]]	        # Or
```

### Conditionals
```bash
if [[ -z ${string} ]]; then
  echo "String is empty"
elif [[ -n ${string} ]]; then
  echo "String is not empty"
fi
```

### Functions
```bash
function get_car() {\
  echo "Kia Forte"
}

get_name() {
  echo "Justin"
}

echo "You are $(get_name)"
```

### Loops
```bash
# Basic
for i in /etc/rc.*; do
  echo "$i"
done

# C-Like
for ((i = 0 ; i < 100 ; i++)); do
  echo "$i"
done

# Ranges
for i in {1..5}; do
    echo "Welcome $i"
done

# Reading lines
while read -r line; do
  echo "$line"
done
```

### Arrays
```bash
Fruits=('Apple' 'Banana' 'Orange')
Fruits[0]="Apple"
Fruits[1]="Banana"
Fruits[2]="Orange"

echo "${Fruits[0]}"     # Element #0
echo "${Fruits[-1]}"    # Last element
echo "${Fruits[@]}"     # All elements, space-separated
echo "${#Fruits[@]}"    # Number of elements
echo "${#Fruits}"       # String length of the 1st element
echo "${#Fruits[3]}"    # String length of the Nth element
echo "${Fruits[@]:3:2}" # Range (from position 3, length 2)
echo "${!Fruits[@]}"

for i in "${arrayName[@]}"; do
  echo "$i"
done
```

### Dictionaries
```bash
declare -A sounds
sounds[dog]="bark"
sounds[cow]="moo"
sounds[bird]="tweet"
sounds[wolf]="howl"
```

### History
```bash
history	# Show history
```

### Expansions
```bash
!$          # Expand last parameter of most recent command
!*          # Expand all parameters of most recent command
!-n         # Expand nth most recent command
!n          # Expand nth command in history
!<command>	# Expand most recent invocation of command
```