---
created: 2023_01_06
updated: 
author: jzw19
tags: 
theme: night
---

<h2>Intro to Golang</h2>
<h4>For the JavaScript-minded</h4>

---
### Table of Contents
1. It's not JavaScript :')
2. Print statements
3. Pointers and Structs
4. Arrays and Slices
5. Testing and Debugging
6. Other Stuff
7. Example Code
---
### It's not JavaScript :')
1. Every Go program is made of packages. Every file belongs to a package, declared at the top of the file
	- `package main`
2. Import statements are grouped together in parentheses when there are multiple imports
	- `import "fmt"`
	- ```import (
		  "fmt"
		  "math/rand"
		)```
3. Functions are declared with the `func` keyword
4. Capitalization matters. When you capitalize the name of a function, you are exporting it.
	- `func Hello` &larr; exported
	- `func hello` &larr; not exported
	- `fmt.Println` &larr; using a function from a package that was imported
5. You don't need (or want) semicolons at the end of each line
---
### It's not JavaScript :') (cont)
6. Variable declaration
	- Declaring variables without assignment
		- `var myVar`
		- `var myVar, myOtherVar`
	- Declaring variables and assigning value(s)
		- `var myVar = 1`
		- `var myVar, myOtherVar = 2, myOtherOtherVar int = 3`
		- `myVar := “flub”`
		- `var myVar, myOtherVar`
7. null is nil
8. Run a function asynchronously by using the go keyword.
	- Need to use the sync package to await go routines 
	  ```
	  import “sync”
	  var wg = sync.WaitGroup{}
	  wg.Add(1)
	  go myAsyncFunction()
	  … (Other code) …
	  wg.Wait()
	  ```
---
### Print Statements

1. Need to import the module "fmt"
2. Probably going to use these the most:
	- `fmt.Print(“blah blah\\n”)`
	- `fmt.Println(“blah blah”)`
	- `fmt.Printf(“insert stuff here: %v”, stuff)`
---
### Pointers and Structs
1. Like C, Go uses pointers and structs
2. Pointers
	- “point” to a location in memory
	- “\*” is used to denote the value in that memory location
		```go
		  var p *int // p is a pointer to an int value
		  *p = 21
		```
	-  “&” is used to denote the memory location of something
	```go
	  i := 42
	  pointer = &i // "pointer" holds the memory location of "i"
	  fmt.Println(pointer) // "0xc000012028"
	  fmt.Println(*pointer) // "42"
	```
---
### Pointers and Structs (cont.)
3. Structs
	- Are _similar_ to custom data types or classes that we define in JavaScript
	- Example:
	  ```go
	  type Vertex struct {
		  X int
		  Y int
	  }
	  func main() {
		  v := Vertex{1, 2}
	  }
```
---
### Arrays and Slices
1. Arrays cannot be resized. An array's length is part of its type.
	- var arr [10]int
		- arr[0:10]
		- arr[:10]
		- arr[0:]
		- arr[:]
2. Slices can be resized.
	- arr[low:high] &rarr; creates a slice from array "arr", including low index and excluding high index
3. Slices do not store any data. They just reference a section of an array (by pointing to a location in memory), so if multiple slices reference sections of the same array, then they will all see changes to that array
---
### Arrays and Slices (cont.)
4. To get something like dynamically sized array, use **make**
```go
a := make([]int, 5)     // len(a) == 5
b := make([]int, 0, 5)  // len(b) == 0, cap(b) == 5, cap = capacity
``` 
5. Append to slices using **append**
```go
append(slice, ...elements)
append(slice, 1)               // appends 1 to slice
append(slice, 1, 2)            // appends 1 and 2 to slice
```
---
### Testing and Debugging
1. You can stop execution on a breakpoint when running tests
	- Some setup is required for this in taco. Follow steps here
2.  You need to have the service under test running locally for the tests to run properly
3. When testing, you will not hit the actual database. Your tests will hit a local database running in a Docker container.
	- Tests that need pre-existing data must create it themselves
4. If trying to make requests from Postman to your local DB to debug an issue, be aware that the data is very different from what is in Hack
	- There is only 1 user
	- You may not be able to stop on a breakpoint (I’m still trying to figure this out)
---
### Other Stuff
1. `go mod tidy` installs packages
2. range function
	1. Used for iterating over a slice or map
```
pow := []int{1, 2, 4, 8, 16}
for index, value := range pow { … }
```
3. Maps
	1. Zero value is nil
	2. Created using make or by using a literal
```
var m map[string]int
…
m[“day”] = 3
```
```
var m map[string]int{
	“day”: 3
}
```
---
### Example Code - Booking App
##### main.go
```
package main

  

import (

  "booking-app/helper"

  "fmt"

  "strconv"

  "sync"

  "time"

)

  

var wg = sync.WaitGroup{}

  

func main() {

  conferenceName := "Go Conference"

  const conferenceTickets uint = 50

  var remainingTickets uint = 50

  bookings := make([]helper.UserData, 0)

  

  // fmt.Printf("conferenceTickets is %T, remainingTickets is %T, conferenceName is %T\n", conferenceTickets, remainingTickets, conferenceName)

  

  helper.GreetUsers(conferenceName, conferenceTickets, remainingTickets)

  

  for {

    var firstName string

    var lastName string

    var email string

    var userTickets uint

  

    // ask user for their name

    firstName, lastName, email, userTickets = helper.GetUserInput(firstName, lastName, email, userTickets)

    // fmt.Printf("\n\nfirstName: %v\nlastName: %v\nemail: %v\nuserTickets: %v\n\n\n", firstName, lastName, email, userTickets)

  

    isUserInputValid := helper.ValidateUserInput(firstName, lastName, email, userTickets, remainingTickets)

    if !isUserInputValid {

      continue

    }

  

    wg.Add(1)

    go sendTicket(userTickets, firstName, lastName, email)

  

    var userData = helper.UserData{

      FirstName:       firstName,

      LastName:        lastName,

      Email:           email,

      NumberOfTickets: strconv.FormatUint(uint64(userTickets), 10),

    }

  

    remainingTickets = remainingTickets - userTickets

    // bookings = append(bookings, firstName+" "+lastName)

    bookings = append(bookings, userData)

  

    helper.PrintBookingInfo(bookings)

    helper.PrintResponseToUser(firstName, lastName, email, conferenceName, userTickets, remainingTickets)

    helper.PrintFirstNames(bookings)

  

    if remainingTickets == 0 {

      fmt.Println("Our conference is booked out. Come back next year.")

      break

    }

  }

  

  wg.Wait()

}

  

func sendTicket(userTickets uint, firstName string, lastName string, email string) {

  time.Sleep(5 * time.Second)

  var ticket = fmt.Sprintf("%v tickets for %v %v", userTickets, firstName, lastName)

  fmt.Println("\n####################")

  fmt.Printf("Sending ticket(s)...\n%v \nsent to email address %v\n", ticket, email)

  fmt.Println("####################")

  wg.Done()

}
```
--
### Example Code - Booking App
##### helper.go
```
package helper

  

import (

  "fmt"

  "strings"

)

  

type UserData struct {

  FirstName       string

  LastName        string

  Email           string

  NumberOfTickets string

}

  

func GreetUsers(conferenceName string, conferenceTickets uint, remainingTickets uint) {

  fmt.Printf("Welcome to %v booking application\n", conferenceName)

  fmt.Printf("We have total of %v tickets and %v are still available.\n", conferenceTickets, remainingTickets)

  fmt.Println("Get your tickets here to attend")

}

  

func GetUserInput(firstName string, lastName string, email string, userTickets uint) (string, string, string, uint) {

  fmt.Print("Enter your first name: ")

  fmt.Scan(&firstName)

  

  fmt.Print("Enter your last name: ")

  fmt.Scan(&lastName)

  

  fmt.Print("Enter your email: ")

  fmt.Scan(&email)

  

  fmt.Print("Enter number of tickets: ")

  fmt.Scan(&userTickets)

  

  return firstName, lastName, email, userTickets

}

  

func ValidateUserInput(firstName string, lastName string, email string, userTickets uint, remainingTickets uint) bool {

  isValidName := len(firstName) >= 2 && len(lastName) >= 2

  isValidEmail := strings.Contains(email, "@") && strings.Contains(email, ".")

  isValidTicketNumber := userTickets > 0 && userTickets <= remainingTickets

  

  if !isValidName {

    fmt.Println("Please input valid first and last names. The minimum acceptable length of each name is 2")

  }

  if !isValidEmail {

    fmt.Println("Please input a valid email address. Email addresses must contain the characters '@' and '.'")

  }

  if !isValidTicketNumber {

    fmt.Printf("We only have %v tickets remaining, so you can't book %v tickets\n", remainingTickets, userTickets)

    fmt.Println("Please try again.")

  }

  

  return isValidName && isValidEmail && isValidTicketNumber

}

  

func PrintBookingInfo(bookings []UserData) {

  fmt.Printf("\nThe whole array: %v\n", bookings)

  fmt.Printf("The first value: %v\n", bookings[0])

  fmt.Printf("Map Type: %T\n", bookings)

  fmt.Printf("Map length: %v\n", len(bookings))

}

  

func PrintResponseToUser(firstName string, lastName string, email string, conferenceName string, userTickets uint, remainingTickets uint) {

  fmt.Printf("\nThank you %v %v for booking %v tickets. You will receive a confirmation email at %v\n", firstName, lastName, userTickets, email)

  fmt.Printf("%v tickets remaining for %v\n\n", remainingTickets, conferenceName)

}

  

func PrintFirstNames(bookings []UserData) {

  firstNames := []string{}

  for _, booking := range bookings {

    firstNames = append(firstNames, booking.FirstName)

  }

  fmt.Printf("The first names of bookings are: %v\n", firstNames)

}
```