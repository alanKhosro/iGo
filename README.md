*BTW: This booklet is in progress. If you would like to contribute email me alan.khosro at gmail.*

# Golang: Programming with Go for beginners
Go is simple by "design". You may say Go is an orthodox religion that denies most of the recent advancement and conventions in software development. You may also say it is Zen for software development.
If you think very sophisticated, you are overthinking in Goland. It needs not much education but it is not very easy to use it either. It is not for casual developer, it aims for smart and elegant software development. 

Python is easy and convenient (comformist), C++/C#/Java are theoritically advanced (academician), C/Pascal are old-style (orthodox), R/Matlab/SQL are niche players (focused), JS/VBasic/Ruby are supporting lnaguages (Auxulary), Go is for genuine programming (Zen).

It has a genuis way to implement parallelism, inheritance, safety, and modularity: four destruptive concepts in the last four decades after the inception of C.

To learn Go, you need to think simple like a Zen master. Forget sophisticated concept like object, class, polymorphism, asynchronism, generics, encapsulation, oop, ...

This booklet for programmers with little (or no) knowledge in programming and it will avoid unnecessary, sophisticated concepts. This booklet encourages you to use the following resources along with this booklet:
- [A Tour Of Go](tour.golang.org): It is an amazing source to learn basics of Go. I assume you already had a tour of go, if not, do not miss it.
- [Go Playground](play.golang.org): Whenever you want to test and learn, you can use this playground. We use it throughout this booklet.
- [Effective Go](golang.org/doc/effective_go.html): After reading this booklet, whenver you need to learn more, effective Go is an effective source.
- [Go Standard Packages](godoc.org/-/go): Go's documentation for standard packages is developed to show how Go works in practice. After you advanced a little, use this source as an ultimate learning resource.

******************
## Hello World
Let us write our first Go program and print "Hello, World":
```go
package main
import "fmt"
func main () {
    fmt.Print("Hello, World.")
}
```
There you go, we printed `Hello, World`.

We needed standard `fmt` package to `Print`. Go, itselg, is very small and most of functions and methods are packaged separately in standard packages that we need to `import` in our programs.

As you noticed, Go is a structured programming language and modularity in R starts with good (obligatory) practices and smart packaging.  
For instance, using `main` is mandotary. `main` declares this is the main package (so it is not a package to be used by other packages) and the function `main` contains the statements to start execution. It is a good practice that Go forces us to follow.

Notice that imported function `Print` starts with capital letter. The capital letter at the beginning, tells Go the function `Print` is exported so Go makes it available for other packages that import `fmt`. So all exported identifiers starts with Capital letter and the rest is for package internal usage and not accessible for others. When writing a package, we need to follow this good practice.

```go
import ("fmt"; "time")


func main () {
    fmt.Print("Hello, World\n","你好, 世界\n", "سلام دنیا", "\nNow time is ", time.Now())
}
``` 


**********
## Data Types
Go is statically-typed language so you can mix integer with string in an statement. Every variable must be declared with its type so that Go knows how to manage its allocated memory and how to handle functions that call that variable.

Go has a variety of boring data types:
```go
bool // to store boolean variable true or false
string // to store string: usual texts
int  int8  int16  int32  int64 rune // to store integers
uint uint8 uint16 uint32 uint64 uintptr byte // to store unsigned integer
float32 float64 // to store decimal numbers
complex64 complex128 // to store complex numbers
/*
uint32 means unsigned integer of 32 bits which covers 0 to 2^32-1 integer numbers.
rune is alias for int32 and represents a Unicode characters. byte is alias for unit8 and represents a byte.
int, unit, and unitptr are 32 bits in 32-bit operating system and 64 bits in 64-bit operating system.
*/
```  

BTW: As you noticed to comment a line `//a line` is used and to comment a text `/* text */` is used.
*********************
## Variables
Let us write our first program:


In Go syntax, you write as you read so to declare   
*variable x of type int with initial value 10*  
you write 
```go
var x int = 10
```



## Interface
Function `fmt.Println` has a secret feature. Try to figure it out through what `fmt.Println` prints for the following program:
```go
package main
import "fmt"
type Human struct {
    name string
    job string
    hubby string
}
func (h Human) String () string {
    return ("Hi, my name is "+h.name+"and I would like to do "+h.hubby+"in my spare time.")
}
func (h Human) Introduce () string {
    return (" Name: "+h.name+"\n Job: "+h.job)
}
func main () {
    h := Human{"Alan", "Developer", "Writing"}
    fmt.Println(h)
}
```
How did `fmt.Println(h)` know to print the return of `h.String()` and not `h.Introduce()`? 
How does a function knows what to do "in future" when facing a new data type? How to write a function that works for a variety of data types? The answer is "through `interface`". `interface` is nothing but a collection of function interfaces (or definitions) but it works like magic.

Let us start with an example: we want a "method" that prints summary for any variable--no matter what data structure it has--that have `Stat()` method. We need to define the interface of `Stat()` in `interface{}` and write our method that receives this `interface{}`.
```go
type stat interface{
    Stat() []float64
}   

func Summary (s stat) {
    nums := s.Stat()
    fmt.Println("For this stat, the average is ", )
}

```



