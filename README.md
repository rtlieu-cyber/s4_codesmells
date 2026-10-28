# s4_codesmells

# Group Members:
Rayden Lieu
Caden Politiski
Keanu Schlank


# Code Smells Chosen:

1. Mysterious Name
2. Shotgun Surgery
3. Feature Envy


# Mysterious Name:
Description:
This code smell refers to the naming of various things like functions, variables, and classes. Having good, clear names for these in your code will help anyone reading your code to easily understand what it is that your function for example is doing inside your code. Reading code can be a headache when you have to go through everything line by line and think about what each piece of code is doing just because you didn't give names that clearly explain your intention. This doesn't just help others when reading your code, proper names also help yourself when going back to your code later on in the future. 
Prevention:
The easiest way to prevent this is to name each function, variable, class, etc. with whatever it is that you intend to use them for. 
Fixes:
If the code smell is already present then you will have refactor your code by changing the names to be fitting for your intentions with each function, class, and variable.
Examples:
C++:
```
before:
class Something2 {
  private:
  public:
}
```
```
after:
class WordSearch {
	private:
	public:
}
```
Java:
```
before:
string Line()
```
```
after:
string errorMessage()
```
Python:
```
before:
def Function()
```
```
after:
def SimpleAddition()
```

# Shotgun Surgery!

Introduction:
	Shotgun Surgery is a code smell wherein in order to make a change, the programmer has to make a lot of small changes in different places. This can arise when the user has a lot of different code that all perform very similar actions. This could be things like repeated calculations or calling a function multiple times when it is unnecessary. 
  Issues may occur when you need to adjust your code, because if you only change one part, the others will still have the old code. This gives the code smell its name, as a shotgun’s individual pellets do not do much, but there are a lot of little pellets. 

Prevention & Refactoring:
  Fowler cites *Move Function, Move Field, Combine Functions into Class, Combine Functions into Transform, Split Phase, Inline Function,* and *Inline Class* as all methods to refactor shotgun surgery. Most of these move code around into things like helper functions or classes, combining redundant code into one place. Essentially, we try to get all the shared code into one place, before deciding if it needs to be split up into helpers.

Code Examples (2 languages):

TypeScript: 
```javascript
function timedgrowth() {
  const _timegrowing = setInterval(() => {
    counter++;
    updateCounter();
  }, 1000);
}

// after refactoring:

function clock() {
  const _time = setInterval(() => {
    propaganda += prop_per_sec;
    updateCounter();
  }, 1000);
}
```
Java:
```java
// In OrderService
decimal tax = order.Subtotal * 0.08m;

// In InvoiceService
decimal tax = invoice.Amount * 0.08m;

// In QuoteService
decimal tax = quote.Total * 0.08m;

// after refactoring:

public class TaxCalculator
{
    private const decimal TaxRate = 0.08m;

    public decimal Calculate(decimal amount) => amount * TaxRate;
}
```


# Feature Envy
- Introduction
When a function in one module spends more time communicating with functions or data inside another module than it does in its own module. This happens when code is placed in the wrong class. An example may be a function in one class calculates a student's average grade using grades stored in another class. This arises when logic is written in a different, open class, instead of the class that owns the data. It's a problem because related data and logic should be kept together. If the class that owns the data changes, the envious function may also need to change. Overall harder to maintain.

- Prevention and Refactoring
-Put new behavior in the class that owns the data.
-When writing or reviewing a function, watch for one object being called repeatedly.
-Shift the envious function to the module holding most of the data. If the whole function wants to be with the data, move it (move function). If only a part of it does, extract that part into its own function then move it (extract function -> move function).

- Examples
``` Python
# Before
class ReportCard:
	def print_average(self, student):
		avg = (student.test1 + student.test2 + student.test3) / 3
		print(student.name, avg)

# class accesses student's test scores to calculate the average

# After
class Student:
	def average(self):
		return (self.test1 + self.test2 + self.test3) / 3

class ReportCard:
	def print_average(self, student):
		print(student.name, student.average())

# class calculates its own average
```
``` Java
//Before
class Mechanic {
	void printSpeed(Car car) {
		System.out.println(car.distance / car.time);
	}
}

/*mechanic accesses car's data to calculate its speed*/

//After
class Car {
	double distance, time;

	double speed() {
		return distance / time;
	}
}

class Mechanic {
	void printSpeed(Car car) {
		System.out.println(car.speed());
	}
}

/*car calculates its own speed*/
```

