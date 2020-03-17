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
Eg: var x int  
Eg: var x, y int  
Types: integer, float, strings
Defining an alias (alternate name) for a type  
Eg: type Celsius float64  
Eg: type IDnum int  
Eg: var temp Celsius 
Eg: var id IDnum 
Initializing variables while declaring 
Eg: var int x = 100 
Eg: var x = 100 
Initializing variables after declaring 
Eg: var x int 
Eg: x = 100
Uninitialized variables will have zero value 
Short variable declaration 
Can perform declaration and initialization together 
Can only do this inside a function  
Eg: x := 100 



