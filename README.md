# learn-golang

## Basic Concepts
### 1. Basic Introduction (Hello World)
Go is a programming language designed for simplicity and efficiency. Let's start by writing your first program: "Hello, World!"  
[Learn more about Go basics](https://go.dev/doc/tutorial/getting-started)  

```go  
package main  

import "fmt"  

func main() {  
    fmt.Println("Hello, World!")  
}  
```  

#### Solo Tasks
1. Change the message to say "Hello, [Your Name]!"  
2. Add another line that says "I am learning Go!"  

---



### 2. Introduction to Data Types  
Go has several basic data types: `string`, `int`, `float64`, and `bool`.  
[Learn more about Go data types](https://go.dev/tour/basics/11)  

```go  
package main  

import "fmt"  

func main() {  
    var name string = "Alice"  
    var age int = 11  
    var height float64 = 4.5  
    var isLearning bool = true  

    fmt.Println("Name:", name)  
    fmt.Println("Age:", age)  
    fmt.Println("Height:", height)  
    fmt.Println("Is Learning Go:", isLearning)  
}  
```  

#### Solo Tasks
1. Change the values of the variables to describe yourself.  
2. Add a new variable for your favorite color and print it.  
3. Try declaring a variable without specifying its type.  

---


### 3. Introduction to If Statements  
If statements allow your program to make decisions.  
[Learn more about if statements](https://go.dev/tour/flowcontrol/1)  

```go  
package main  

import "fmt"  

func main() {  
    age := 11  

    if age < 13 {  
        fmt.Println("You are a child.")  
    } else {  
        fmt.Println("You are a teenager or older.")  
    }  
}  
```  

#### Solo Tasks
1. Add a condition to check if the age is between 13 and 19
2. Add a condituon to check if the age is above 21
3. Add a conditon to check whether or not the age is even or odd

---

### 4. Using Command-Line Arguments  
Command-line arguments allow you to pass information to your program when you run it.  
[Learn more about command-line arguments](https://pkg.go.dev/os#Args)  

```go  
package main  

import (  
    "fmt"  
    "os"  
)  

func main() {  
    if len(os.Args) < 2 {  
        fmt.Println("Usage: go run main.go [your name]")  
        return  
    }  

    name := os.Args[1]  
    fmt.Printf("Hello, %s!\n", name)  
    fmt.Println("I am learning Go!")  
}  
```  

#### Solo Tasks  
1. Modify the program to accept a second argument for your age and print it.  
2. Add a condition to check if no arguments are provided and display a helpful message.  
3. Experiment with passing multiple arguments and printing them all.  

---

### 5. Introduction to Functions  
Functions are reusable blocks of code. They help organize your program.  
[Learn more about functions](https://go.dev/tour/basics/4)  

```go  
package main  

import "fmt"  

func greet(name string) {  
    fmt.Println("Hello,", name)  
}  

func main() {  
    greet("Alice")  
}  
```  

#### Solo Tasks
1. Modify the `greet` function to include the person's age.  
2. Write a new function that adds two numbers and prints the result.  
3. Call your new function in the `main` function.  

---


### 6. Introduction to Switch Statements  
Switch statements allow you to simplify multiple conditional checks.  
[Learn more about switch statements](https://go.dev/tour/flowcontrol/2)  

```go  
package main  

import "fmt"  

func main() {  
    day := "Monday"  

    switch day {  
    case "Monday":  
        fmt.Println("Start of the work week.")  
    case "Friday":  
        fmt.Println("Almost the weekend!")  
    case "Saturday", "Sunday":  
        fmt.Println("It's the weekend!")  
    default:  
        fmt.Println("It's a regular weekday.")  
    }  
}  
```  

#### Solo Tasks  
1. Modify the program to include a case for your favorite day of the week.  
2. Add a case that checks for multiple days (e.g., "Tuesday" and "Thursday").  
3. Write a program that uses a switch statement to categorize a number as positive, negative, or zero.  

---

### 7. Introduction to Loops  
Loops let you repeat actions in your program.  
[Learn more about loops](https://go.dev/tour/flowcontrol/3)  

```go  
package main  

import "fmt"  

func main() {  
    for i := 1; i <= 5; i++ {  
        fmt.Println("Count:", i)  
    }  
}  
```  

#### Solo Tasks
1. Write a loop that prints numbers from 10 to 1.  
2. Create a loop that prints all even numbers between 1 and 20.  
3. Use a `while`-like loop (a `for` loop with a condition) to keep asking for input until the user types "stop".  

---

### 8. Introduction to Tests  
Tests ensure your code works as expected.  
[Learn more about testing](https://go.dev/doc/tutorial/add-a-test)  

```go  
package main  

func add(a, b int) int {  
    return a + b  
}  
```  

Test File:  
```go  
package main  

import "testing"  

func TestAdd(t *testing.T) {  
    result := add(2, 3)  
    if result != 5 {  
        t.Errorf("Expected 5, got %d", result)  
    }  
}  
```  

#### Solo Tasks
1. Write a test for a function that multiplies two numbers.  
2. Add a test for a function that checks if a number is even.  
3. Run your tests and fix any errors.  

---

### 9. CLI Calculator

#### Task  
Create a command-line calculator that:  
1. Asks the user for two numbers.  
2. Asks the user for an operation (+, -, *, /).  
3. Performs the operation and prints the result.  
4. Repeats until the user types "exit".  

---

## Advanced Concepts
### 1. Introduction to Structs and Methods  

Go does not have classes, but you can use structs and methods to achieve similar functionality.  
[Learn more about structs and methods](https://go.dev/tour/methods/1)  


```go  
package main  

import "fmt"  

type Person struct {  
    Name string  
    Age  int  
}  

func (p Person) Greet() {  
    fmt.Printf("Hello, my name is %s and I am %d years old.\n", p.Name, p.Age)  
}  

func main() {  
    person := Person{Name: "Alice", Age: 11}  
    person.Greet()  
}  
```  

##### Solo Tasks
1. Add a new field to the `Person` struct for the person's favorite hobby.  
2. Write a method that prints the person's hobby.  
3. Create multiple `Person` instances and call their methods.  

---

### 2. Creating, Reading, and Writing a File  

Go provides tools to work with files for reading and writing data.  
[Learn more about file handling](https://pkg.go.dev/os#pkg-index)  


```go  
package main  

import (  
    "fmt"  
    "os"  
)  

func main() {  
    file, err := os.Create("example.txt")  
    if err != nil {  
        fmt.Println("Error creating file:", err)  
        return  
    }  
    defer file.Close()  

    file.WriteString("Hello, Go!")  
    fmt.Println("File written successfully.")  
}  
```  

##### Solo Tasks
1. Modify the program to read the content of the file and print it.  
2. Write a program that appends text to an existing file.  
3. Handle errors gracefully when the file does not exist.  

---

### 3. Basic Web Server Functionality  

Go makes it easy to create web servers using the `net/http` package.  
[Learn more about web servers](https://pkg.go.dev/net/http)  


```go  
package main  

import (  
    "fmt"  
    "net/http"  
)  

func handler(w http.ResponseWriter, r *http.Request) {  
    fmt.Fprintln(w, "Welcome to my web server!")  
}  

func main() {  
    http.HandleFunc("/", handler)  
    fmt.Println("Starting server on :8080...")  
    http.ListenAndServe(":8080", nil)  
}  
```  

##### Solo Tasks
1. Modify the handler to display a personalized message based on a query parameter (e.g., `?name=Alice`).  
2. Add a new route that displays the current date and time.  
3. Create a simple HTML page and serve it using your web server.  

---

### 4. Advanced Web Server Functionality (HTML + CSS)  

You can serve HTML and CSS files to create more interactive web pages.  
[Learn more about serving files](https://pkg.go.dev/net/http#FileServer)  


```go  
package main  

import (  
    "net/http"  
)  

func main() {  
    fs := http.FileServer(http.Dir("./static"))  
    http.Handle("/", fs)  

    http.ListenAndServe(":8080", nil)  
}  
```  

##### Solo Tasks
1. Create a `static` folder with an `index.html` file and serve it.  
2. Add a CSS file to style your HTML page.  
3. Create a form in your HTML page and handle its submission in Go.  

---

### 5. Introduction to Interfaces  

Interfaces define a set of methods that a type must implement.  
[Learn more about interfaces](https://go.dev/tour/methods/9)  


```go  
package main  

import "fmt"  

type Shape interface {  
    Area() float64  
}  

type Circle struct {  
    Radius float64  
}  

func (c Circle) Area() float64 {  
    return 3.14 * c.Radius * c.Radius  
}  

func main() {  
    var s Shape = Circle{Radius: 5}  
    fmt.Println("Area of the circle:", s.Area())  
}  
```  

##### Solo Tasks
1. Create a `Rectangle` struct and implement the `Shape` interface.  
2. Write a function that takes a `Shape` and prints its area.  
3. Add another method to the `Shape` interface and implement it for both `Circle` and `Rectangle`.
