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

#### Assessment
1. trunc.go  
Write a program which prompts the user to enter a floating point number and prints the integer which is a truncated version of the floating point number that was entered. Truncation is the process of removing the digits to the right of the decimal place.  

2. findian.go  
Write a program which prompts the user to enter a string. The program searches through the entered string for the characters ‘i’, ‘a’, and ‘n’. The program should print “Found!” if the entered string starts with the character ‘i’, ends with the character ‘n’, and contains the character ‘a’. The program should print “Not Found!” otherwise. The program should not be case-sensitive, so it does not matter if the characters are upper-case or lower-case.  

Examples: The program should print “Found!” for the following example entered strings, “ian”, “Ian”, “iuiygaygn”, “I d skd a efju N”. The program should print “Not Found!” for the following strings, “ihhhhhn”, “ina”, “xian”.  

### Composite Data Types  
#### Arrays 
Fixed-length series of elements of a chosen type  
Elements initialized to zero value  
<pre>
var x [5]int 

x[0] = 2 
fmt.Printf(x[1]) 
</pre>
Array literal is an array pre-defined with values  
... for size in array literal infers size from number of initializers  
<pre>
var x [5]int = [5]{1, 2, 3, 4, 5}

y := [...]int{1, 2, 3, 4}
</pre> 
Iterating through an array  
<pre>
x := [3]int {1, 2, 3}

for i, v range x { 
  fmt.Printf("index %d, value %d", i, v) 
}
</pre>  

#### Slices 
Slice is an window on an underlying array  
Variable size, up to the whole array  
Every slice has 3 properties 
1. pointer - indicates the start of the slice  
2. length - number of elements in the slice  
3. capacity - maximum number of elements in the slice  
<pre>
arr := [...]string{"a", "b", "c", "d", "e", "f", "g"}
s1 := arr[1:3]
s2 := arr[2:5]  
</pre>  
len() and cap() functions  
<pre>
a1 := [3]string{"a", "b", "c"} 
slil := a1[0:1]
fmt.Printf(len(slil), cap(slil))
</pre>
Slice Literals  
<pre>
sli := []int{1, 2, 3}
</pre>

#### Variable Slices 
make() creates a slice (and array)  
2-argument version: specify type and length/capacity  
<pre>
sli = make([]int, 10) 
</pre>
3-argument version: specify type, length and capacity  
<pre>
sli = make([]int, 10, 15) 
</pre>  
Append  
\- Adds elements to the end of a slice  
\- Inserts into underlying array  
\- Increases size of array if necessary  
<pre>
sli = make([]int, 0, 3)
sli = append(sli, 100)
</pre>

#### Hash Tables
Contains key/value pairs  
Faster lookup than lists  
Arbitary keys  
May have collisions  

#### Maps 
Go lang implementation of hash table  
<pre>
var idMap map[string][int] //string = key type, int = value type 
idmap = make(map[string]int) 
</pre>
Map Literal  
<pre>
idMap := map[string]int {"joe": 123 } 
</pre>
Accessing Maps  
<pre>
fmt.Printf(idMap["joe"]) 
idMap["jane"] = 345 
delete(idMap, "joe")
</pre>
Map Functions  
<pre>
id, p := idMap["joe"]
// id is value, p is presence of key (boolean) 
fmt.Printf(len(idMap)) // length of map 

// Iterating 
for key, val := range idMap { 
  fmt.Println(key. val) 
}
</pre>

#### Structs
Aggregate data type  
Groups together other objects of arbitary type  


<pre>
type struct Person {
  name string 
  addr string 
  phone string 
}

var p1 Person 

p1.name = "joe"
x = p1.addr
</pre>
Initializing structs  
Using new() function  
Initializes fields to zero 
<pre>
p1 := new(Person) 
</pre>
Using struct literals  
<pre>
p1 := Person(name: "joe", addr: "a street",
      phone: "123")
</pre>  

#### Assessments 
1. slice.go 
Write a program which prompts the user to enter integers and stores the integers in a sorted slice. The program should be written as a loop. Before entering the loop, the program should create an empty integer slice of size (length) 3. During each pass through the loop, the program prompts the user to enter an integer to be added to the slice. The program adds the integer to the slice, sorts the slice, and prints the contents of the slice in sorted order. The slice must grow in size to accommodate any number of integers which the user decides to enter. The program should only quit (exiting the loop) when the user enters the character ‘X’ instead of an integer.  

### Protocols and Formats  
#### RFCs
Request For Comments  
Definitions of Internet Protocols and formats  
Golang provides packages for important RFCs  
These packages provides functions which encode and decode protocol formats  
Examples:  
"net/http" - web communication protocol   
http.Get(www.abc.com)  
"net" - TCP/IP and socket programming  
net.Dial("tcp", "example.com:80")  

#### JSON
JSON Properties  
\- All unicode  
\- Human-readable  
\- Fairly compact representation  
\- Types can be combined recursively  
(Array of structs, struct in struct)  
JSON Marshalling  
JSON Marshalling is generating JSON object from go objects  
Marshal() returns JSOn representation as []byte (byte array)  
Unmarshal() converts a JSON []byte into a Go object  
Pointer to a Go object is passed to Unmarshal()  
Go object should fit JSON []byte 
<pre>
type struct Person {
  name string 
  addr string 
  phone string 
}

json.Marshal(p1)

var p2 Person 
err := json.Unmarshal(barr, &p2) 
</pre>

#### File Access, ioutil
Linear access, not random access  
Basic operations  
\- Open => get handle for access  
\- Read => read bytes into []byte  
\- Write => write []byte into file  
\- Close => release handle  
\- Seek => move read/write head  
ioutil package - "io/ioutil"  
Explicit open/close not required  
Large files cause a problem, it reads into main memory  
<pre>
// returns data (byte array) and error (if any)
dat, e := ioutil.ReadFile("test.txt") 

// WriteFile 
dat = "Hello World"
err := ioutil.WriteFile("outfile.txt", dat, 0777)
</pre>

#### File Access, os 
os package  
\- os.Open() 
\- os.Close() 
\- os.Read() 
\- os.Write() 
<pre>
f, err := os.Open("data.txt") // opens file, returns file handle f 
barr := make([]byte, 10) // creates a byte array of length 10 bytes 
nb, err := f.Read(barr) // reads first 10 bytes into byte array 
f.Close() // close the file handle 
</pre>  

<pre>
f, err := os.Create("new.txt") // create a file handle to write 
barr := []byte{1, 2, 3} // make a slice 
nb, err := f.Write(barr) 
nb, err := f.WriteString("Hi") 
</pre>  

#### Assessments 
1. makejson.go  
Write a program which prompts the user to first enter a name, and then enter an address. Your program should create a map and add the name and address to the map using the keys “name” and “address”, respectively. Your program should use Marshal() to create a JSON object from the map, and then your program should print the JSON object.  
2. read.go  
Write a program which reads information from a file and represents it in a slice of structs. Assume that there is a text file which contains a series of names. Each line of the text file has a first name and a last name, in that order, separated by a single space on the line.  

Your program will define a name struct which has two fields, fname for the first name, and lname for the last name. Each field will be a string of size 20 (characters).  

Your program should prompt the user for the name of the text file. Your program will successively read each line of the text file and create a struct which contains the first and last names found in the file. Each struct created will be added to a slice, and after all lines have been read from the file, your program will have a slice containing one struct for each line in the file. After reading all lines from the file, your program should iterate through your slice of structs and print the first and last names found in each struct.  

