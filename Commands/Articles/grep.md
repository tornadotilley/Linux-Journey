`grep` is a program that finds text patterns within files. When it finds the pattern within a file, it will then print the matching string as output. It is written like this:

`[ttilley@somelinux ~]$ grep "red" colors.txt`

With a -r if it is a directory:

`[ttilley@somelinux ~]$ grep -r "red" ~/colors/`

There are many great ways to use grep with the `*` (wildcard) operator. 

`[ttilley@somelinux ~]$ grep -r "*red" ~/colors/`

### Flags

These are just a few flags for grep that might come in handy.
- `-E` - grep will behave like `egrep`, accepting extended regular expressions
- `-i` - grep ignores case when performing the search
- `-l` - grep will only print the names of the files that contain the text
- `-L` - Prints the names of the files that do not contain any matches
- `-v` - grep will only print lines that do not match the text pattern
- `-w` - grep will only match whole words 
- `-c` - grep only prints the number of matches
- `-n` - prefixes each line with the line number 
- `-h` - suppresses the output of each file name
- `-q` - suppress all output (will be useful in scripting)

### Metacharacters
These are the characters that we will be using for more robust matching. **They must all be enclosed in quotes.** 

- `.` - 'The any character'; matches any character that is in that position. 
	- ```
	  [ttilley@somelinux ~]$ grep -h '.zip' dirlist*.txt
	  ```

- `^` & `$` - 'Anchors'; the matches must occur at the beginning of the line or the end of the line
	- 
	  ```
	  [ttilley@somelinux ~]$ grep -h '^zip' dirlist*.txt
	  ```
	  This will show lines where zip is at the beginning of the line
	```
	[ttilley@somelinux ~]$ grep -h 'zip$' dirlist*.txt
	```
This will show the lines where zip is at the end

- `[]` - 'Bracket expression'; within the brackets, we can use a set of letters to be matched. 
	- ```
	  [ttilley@somelinux ~]$ grep -h '[bg]zip' dirlist*.txt
	  ```
	  This will bring up any matches that contain these two characters in their place. 
	- **This indicates that a character must be present in front of the search term.**
	- Using the `^` within the brackets indicates negation, meaning any character that is not these two will be matched. 
	- Using the `-` within the brackets indicates a range of characters

Here will be a list of POSIX character classes:
![[Pasted image 20260108082441.png]]
![[Pasted image 20260108082504.png]]

# ~={green}Extended Regular Expressions=~ 
### Alternation
Alternation allows a match to occur from a set of regular expressions. This can be written like this:
```
[ttilley@somelinux ~]$ echo "AAA" | grep -E 'AAA|BBB'
AAA 
```
Here, we gave the choice of two expressions for matching, and the correct one matched. We can add more expressions if we want to:
```
[ttilley@somelinux ~]$ echo "AAA" | grep -E 'AAA|BBB|CCC'
AAA 
```
We can see how this might be more useful, if we were to need to find many kinds of zip files in our directories:
```
[ttilley@somelinux ~]$ grep -E 'bz|gz|zip' dirlist*.txt
```
This can even be used with other elements of regular expressions, by enclosing it in parenthesis:
```
[ttilley@somelinux ~]$ grep -E '^(bz|gz|zip)' dirlist*.txt
```

---
## Quantifiers
Quantifiers allow us to specify the number of times that a certain character is matched. 
### `?`
For the `?` quantifier, this will indicate that the preceding character is to be matched one or zero times. 
```
[ttilley@somelinux ~]$ echo "(555) 123-4567" | grep -E '^\(?[0-9][0-9][0-9]  
\)? [0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]$'  
(555) 123-4567  
[ttilley@somelinux ~]$ echo "555 123-4567" | grep -E '^\(?[0-9][0-9][0-9]\)  
? [0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]$'  
555 123-4567  
[ttilley@somelinux ~]$ echo "AAA 123-4567" | grep -E '^\(?[0-9][0-9][0-9]\)  
? [0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]$'  
[ttilley@somelinux ~]$
```
Here, we have written a phone number, and made sure that it is valid. We have escaped the parenthesis to make sure that the shell will interpret them as literals. We then test that each character is a number, with `[0-9]`. This will not work if we decide that we need the parenthesis around the first three numbers. 

## `*`
`*` means that we want to match the preceding character zero or more times.  
```
[ttilley@somelinux ~]$ echo "This works." | grep -E '^[[:upper:]][[:upper:]  
[:lower:] ]*\.'  
This works.  
[ttilley@somelinux ~]$ echo "This Works." | grep -E '^[[:upper:]][[:upper:]  
[:lower:] ]*\.'  
This Works.  
[ttilley@somelinux ~]$ echo "this does not" | grep -E '^[[:upper:]][[:upp  
er:][:lower:] ]*\.'  
[ttilley@somelinux ~]$
```
When we specify that the preceding bracket expansion is to be matched zero or more times, but we have also specified that we need there to be an uppercase character in the first place. 

## `+`
`+` works like the `*` character, but it requires at least one instance of the character (one or more times). 


```
[ttilley@somelinux ~]$ echo "This works." | grep -E '^[[:upper:]][[:upper:]  
[:lower:] ]*\.'  
This works.  
[ttilley@somelinux ~]$ echo "This Works." | grep -E '^[[:upper:]][[:upper:]  
[:lower:] ]*\.'  
This Works.  
[ttilley@somelinux ~]$ echo "this does not" | grep -E '^[[:upper:]][[:upp  
er:][:lower:] ]*\.'  
[ttilley@somelinux ~]$
```

## `{}`
`{}` are used to express the minimum and the maximum of required matches. The preceding element is must occur '{*n*}' or more times. Below is a chart and example of how to use this. 

![[Pasted image 20260111194605.png]]

```
[ttilley@somelinux ~]$ echo "(555) 123-4567" | grep -E '^\(?[0-9]{3}\)? [0-  
9]{3}-[0-9]{4}$'  
(555) 123-4567  
[ttilley@somelinux ~]$ echo "555 123-4567" | grep -E '^\(?[0-9]{3}\)? [0-9]  
{3}-[0-9]{4}$'  
555 123-4567  
[ttilley@somelinux ~]$ echo "5555 123-4567" | grep -E '^\(?[0-9]{3}\)? [0-9  
]{3}-[0-9]{4}$'  
[ttilley@somelinux ~]$
```

## Searching text documents. 
Certain text editors support regular expressions for finding text. **Thats so cool!!!!!!** 













































