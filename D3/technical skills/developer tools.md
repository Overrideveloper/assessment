# Developer Tools

### xargs
Is a command on Unix and most Unix-like operating systems used to read streams of data from standard input. It takes the output of a command and passes it as argument of another command.

```
>>> echo {1..9} | xargs -n 2 echo "Hello World"

Hello World 1 2
Hello World 3 4
Hello World 5 6
Hello World 7 8
Hello World 9
```

### expr
expr is a command line Unix utility which evaluates an expression and outputs the corresponding value.

```
>>> expr 6 "<" 2

0
```
The output here is 0 because 6 is actually greater than 2

### AWK
AWK is an interpreted programming language. It is very powerful and specially designed data extraction and for text processing. 

Example: lets consider a text file marks.txt to be processed with the following content
```
1) Amit     Physics   80
2) Rahul    Maths     90
3) Shyam    Biology   87
4) Kedar    English   85
5) Hari     History   89
```

This command prints the third line in the file.
```
>>>  awk 'FNR == 2 {print}' score.txt
```

**output**
```
3) Shyam    Biology   87
```


### sed
sed is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline).

For example, to replace all occurrences of ‘hello’ to ‘world’ in the file input.txt:

```
>>> sed 's/hello/world/' input.txt > output.txt
```