# CONTRIBUTING
The purpose of this guideline is to define what functions should be included in this repository, and how to include them.

## What is an Insecure Function ?
Any function that introduces a vulnerability to the program by itself or when it receives an user-controlled parameter. The vulnerability should be well-documented and not informative.

### Vulnerabilities

Here's a list of vulnerabilities that we included so far, if you think on a vulnerability that should be included open an Issue.

| Vulnerability | Filename |
|---------------|----------|
| Buffer Overflow| bof.txt |
| Heap Overflow | heap.txt |
| Insecure Deserialization | deserialization.txt |
| Local File Include | lfi.txt |
| Remote Command Execution | rce.txt |
| Server Side Request Forgery | ssrf.txt |
| Server Side Template Injection | ssti.txt |
| Cross-Site Scripting | xss.txt|
| SQL Injection | sqli.txt |

### Exceptions
If a function needs special arguments or configurations to be insecure this should be debated per case.

## How to represent the Function ?
As the goal of the project is to assist code reviews, the lists should contain a minimal and unambiguous string that represents the function.
This should make it easy for the hacker to search for this string on his source code. The list should also be script friendly.

### Minimal 
A minimal representation of the Insecure Function should be a string that when searched on the source code only finds Insecure Functions, with some exceptions.

Example :
```python
eval(input("Enter a math expression: "))
```
Should be included on the `/python/rce.txt` file as
```
eval
```

### Unambiguous
Sometimes a Function is included on more than one lib, on those cases the lib name should be also included on the file. 

Example:
```golang
   resp, err := http.Get("https://google")
```
As `Get` maybe appears on other contexts and it's a fairly common string, we need to include the whole `http.Get` on `/golang/ssrf.txt`
