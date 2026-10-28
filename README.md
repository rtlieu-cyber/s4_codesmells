# s4_codesmells

group members:
Rayden Lieu
Caden Politiski
Keanu Schlank

code smells chosen:
shotgun surgery
mysterious name
feature envy


Mysterious Name:
Description:
This code smell refers to the naming of various things like functions, variables, and classes. Having good, clear names for these in your code will help anyone reading your code to easily understand what it is that your function for example is doing inside your code. Reading code can be a headache when you have to go through everything line by line and think about what each piece of code is doing just because you didn't give names that clearly explain your intention. This doesn't just help others when reading your code, proper names also help yourself when going back to your code later on in the future. 
Prevention:
The easiest way to prevent this is to name each function, variable, class, etc. with whatever it is that you intend to use them for. 
Fixes:
If the code smell is already present then you will have refactor your code by changing the names to be fitting for your intentions with each function, class, and variable.
Examples:
C++:
class Something2 {
  private:
  public:
}
Java:
string Words()
Python:
def Function()
