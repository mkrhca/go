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

