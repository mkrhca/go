# go
Advantages  
1. Code runs fast 
2. Garbage collection  
3. Simpler objects  

#### Objects 
Weakly object-oriented  
User-defined types  
Types have data and functions  
Go does not use the term 'class'. Instead it uses 'structs'  
Struct is just the different types of data you want to associate together  
Doesnt have inheritance, constructors, and generics  

#### Concurrency  
Big advantage of Go is concurrency  
Moore's Law  
Implementing parallelism in programming  
Go routines represents concurrent tasks, basically thread  
Go channels are used for communication between concurrent tasks  
Go select is used to enable synchronization  


#### Installing  
1. wget https://dl.google.com/go/go1.14.linux-amd64.tar.gz  
2. tar -C /usr/local -xzf go1.14.linux-amd64.tar.gz  
3. echo 'export PATH=$PATH:/usr/local/go/bin' >> /etc/profile  
4. source /etc/profile  
5. Create hello.go 
<pre>
cat hello.go
package main  

import "fmt"  

func main() {  
        fmt.Printf("hello, world\n")  
}  
</pre>
6. go build hello.go  
7. ./hello 

#### Workspace and Packages 
Your Go source files and other files will go in this workspace directory  
Workspace contains 3 sub-directories 
- source
- package 
- bin  
The workspace directory is defined by the GOPATH environment variable   
A package is a group of related source code files  
Each package can be imported by other packages  
There must be one package called main where execution begins  

#### Go Tool 
Go tool searches GOROOT and GOPATH to find imported packages 
go build - compiles the program  
go build creates an executable for the main package 
go doc - prints documentation for the package 
go fmt - formats source code files  
go get - downloads packages and installs them  
go list - list all installed packages 
go run - compiles the go file and runs the executable  
go test - runs tests (files ending with _test.go)

#### Variables 
Naming 
Dont use keywords  
Variables must have a name and a type  
All variables must be declared  
<pre>  
var x int  
var x, y int  
</pre>
Types: integer, float, strings  
Defining an alias (alternate name) for a type  
<pre>
type Celsius float64  
type IDnum int  
var temp Celsius   
var id IDnum  
</pre>
Initializing variables while declaring  
<pre>
var int x = 100  
var x = 100   
</pre>
Initializing variables after declaring   
<pre>
var x int  
x = 100  
</pre>
Uninitialized variables will have zero value   
Short variable declaration   
Can perform declaration and initialization together  
Can only do this inside a function  
<pre>
x := 100   
</pre>  

#### Assessment 
Download and install the Go tools on your machine. Write a Go program to print “Hello, world!” on the screen. Compile and run the program.  

#### Pointers 
Pointer is an address to data in memory  
& operator returns the address of a variable/function  
\* operator returns data at an address (dereferencing)  
Example
<pre>
var x int = 1 
var y int 
var ip *int // ip is pointer to int 
ip = &x // ip now points to x 
y = *ip // y is now 1 
</pre>
new() function creates a variable and return a pointer to that variable 
variable is initialized to zero 
Example
<pre>
ptr := new(int) 
*ptr = 3 
</pre>

#### Variable Scope 
The places in code where a variable can be accessed  
<pre>
var x = 4 

func f() {
  fmt.Printf("%d", x)
}
func g() { 
  fmt.Printf("%d", x)
}
</pre>  

<pre>
func f() {
  var x = 4 
  fmt.Printf("%d", x)
}
func g() { 
  fmt.Printf("%d", x)
}
</pre>  

Variable scoping is done using blocks  
Implicilt Blocks  
\- Universe Block => all go source  
\- Package Block => all source in a package  
\- File Block => all source in a file  
\- if, for, switch statements => all code inside the statement  
\- Clause in switch or select => individual clauses each get a block  
Lexical Scoping using blocks  

#### Deallocating Memory 
Stacks vs Heap  
Stack - Area of memory dedicated to function calls  
\- Local variables are stored here  
\- Deallocated after function completes  
Heap - Persistent region of the memory  
Data on heap must be deallocated explicitly on languages like C  
Example:  
<pre>
x = malloc(32); 
free(x);
</pre>  
This is error-prone but fast  
In interpreted language, deallocation of memory is done by the interpreter  

#### Garbage Collection 
Hard to determine when a variable is no longer in use  
Example:  
<pre> 
func foo() *int { 
  x := 1 
  return &x // returns pointer to xx  
}

func main() { 
  var y *int 
  y = foo() 
  fmt.Print("%d", *y)
}
</pre>  
Go is a compiled language which enables garbage collection  
Compiler determines stack vs heap  
Garbage collection in the background  

#### Comments and Printing 
Single line comments 
<pre>
//This is a comment  
</pre>  
Block Comments  
<pre>
/* comment 1 
   comment 2 */
</pre> 
Printing  
<pre>
fmt.Printf("Hi") 
x := "Joe" 
fmt.Printf("Hi " + x) 
</pre>  
Format strings 
<pre>
x := "Joe"
fmt.Printf("Hi %s", x)
</pre>  


#### Ints, Floats, Strings 
Generic int declaration  
var x int  
Different lenghts and signs  
int8, int16, int32, int64  
uint8, uint16, uint32, uint64  
Type Conversions  
This will fail  
<pre>
var x int32 = 1 
var y int16 = 2 
x = y 
</pre>
Convert type with T() operation  
<pre>
x = int32(y) 
</pre>  
Floating Point  
float32 => ~6 digits of precision  
float32 => ~12 digits of precision  
ASCII and Unicode  
'A' = 0x41  // ASCII is 8-bit code  
Unicode is 32 bit character code // 2^32  
UTF-8 8-bit code, can go upto 32 bit  
Code point = unicode characters  
Rune = a code point in Go  
Strings are read-only  
String literal is notated by double quotes  

#### String Packages  
Unicode Package provides a set of functions to test categories of runes  
\- IsDigit(r rune)  
\- IsSpace(r rune)  
\- IsLetter(r rune)  
\- IsLower(r rune)  
\- IsPunct(r rune)  
Some functions perform conversions  
\- ToUpper(r rune)  
\- ToLower(r rune)  
Strings package provides functions to manipulate UTF-8 encoded strings  
String search functions  
\- Compare(a,b)  
\- Contains(s, substr)  
\- HasPrefix(s, prefix)  
\- Index(s, substr)  
String Manipulation  
\- Replace(s, old, new, n)  
\- ToLower(s)  
\- ToUpper(s)  
\- TrimSpace(s)  
Strconv package converts to and from string representations of basic data types  
\- Atoi(s)  
\- FormatFloat(f, fmt, prec, bitSize)  
\- ParseFloat(s, bitSize)  

#### Constants
Constant => Expression whose value is known at compile time  
Type is inferred from the RHS  
<pre>
const x = 1.3 
const (
  y = 4 
  z = "Hi"
)
</pre>  
iota is a function to generate a set of related but distinct constants  
Like an enumerated type in other languages  
Example  
<pre>
type Grades int 
const ( 
  A Grades = iota 
  B
  C
  D
  E
  F
)
</pre>  

#### Control Flow 
if statement  
<pre>
if x > 5 { 
  fmt.Printf("Hii\n")
}
</pre>
for loops  
<pre>
for i=0; i<10; i++ {
  fmt.Printf("hi ")
}

i = 0 
for i < 10 { 
  fmt.Printf("hi ") 
  i++ 
}

for { 
  fmt.Printf("hi ") // infinite loop 
}
</pre>  
Switch/Case  
Breaks automatically when matched  
<pre>
switch x {
case 1:
  fmt.Printf("case 1")
case 2:
  fmt.Printf("case 2")
default: 
  fmt.Printf("nocase")
}
</pre>  
Tagless Switch  
<pre>
switch {
case x > 1:
  fmt.Printf("case 1")
case x < -1:
  fmt.Printf("case 2")
default: 
  fmt.Printf("nocase")
}
</pre>  
Break and Continue  
<pre>
i := 0 
for i < 10 { 
  i++ 
  if i == 5 { break } 
  fmt.Printf("hi ")
}
</pre>  
<pre>
i := 0 
for i < 10 { 
  i++ 
  if i == 5 { continue } 
  fmt.Printf("hi ")
}
</pre>  
Scan 
\- Scan reads user input  
\- Takes a pointer as an argument  
\- Typed data is written to pointer  
\- Returns number of scanned items  
<pre>
var appleNum int 

fmt.Printf("Number of apples?") 
num, err := fmt.Scan(&appleNum) 
fmt.Printf(appleNum) 
</pre>

#### 




