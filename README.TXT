Project: clock-display
Authors: David Barnes and Michael Kölling

This project is part of the material for the book

   Objects First with Java - A Practical Introduction using BlueJ
   Seventh edition
   David J. Barnes and Michael Kölling

It is discussed in chapter 3.

To use this project, create an instance of class ClockDisplay. Then inspect this 
instance and leave the object inspector window open. With the inspector window open, 
call the object's methods, such as timeTick and setTime. Watch the 
"displayString" in the inspector.

The displayString field simulates the actual clock display device. Were this 
program running in a real clock, it would change the real, physical display 
hardware instead of this string. The timeTick method would be triggered once 
every minute by some timer hardware.

Everything else could be pretty much the same.


Note: This project does not implement adequate handling of errors.

Lab raport for part 2 of Week 3 (part a = question, part b = answer)

21a. Open the clock-display project and create a ClockDisplay object by selecting 
the following constructor:
 new ClockDisplay()
Call its getTime method to find out the initial time the clock has been set to.
Can you work out why it starts at that particular time?

21b.

22a. Open an inspector for this object. With the inspector open, call the object’s 
methods. Watch the displayString field in the inspector. Read the project comment 
(by double-clicking the text icon in the class diagram) for more information.

22b

23a. How many times would you need to call the timeTick method on a newly created 
ClockDisplay object to make its time reach 01:00? How else could you make it display 
that time?

23b.

24a. Write down the definition of a variable of type NumberDisplay called digit. 
Write an assignment statement that creates a NumberDisplay object with a rollover 
limit of 10 and assigns the object to the variable.

24b.

25a. Write Java statements that define a variable named window of type Rectangle, 
and then create a rectangle object and assign it to that variable. The rectangle 
constructor has two int parameters for the lengths of its sides.

25b.

26a. Look at the second constructor in ClockDisplay’s source code. Explain what it 
does and how it does it.

26b.

27a. Identify the similarities and differences between the two constructors. 
Why is there no call to updateDisplay in the second constructor, for instance?

27b.

28a. Given a variable
 Printer p1;
which currently holds a reference to a printer object, and two methods inside 
the Printer class with the headers.
 public void print(String filename, boolean doubleSided)
 public int getStatus(int delay)
write two possible calls to each of these methods.

28b.

29a. Open the house project from chapter 1 and review the Picture class. What 
types of object are created by the constructor of Picture?

29b.

30a. List all the external method calls that are made in the draw method of Picture 
on the Triangle object called roof.

30b.

31a. Does the Picture class contain any internal method calls?

31b.

32a. What is the result of the expression (8 % 3)? In other words, what value 
remains when 8 is divided by 3?

32b.

33a. Try out the expression (8 % 3) in the Code Pad. Try other numbers. What happens 
when you use the modulo operator with negative numbers?

33b.

34a. What are all possible results of the expression (n % 5), where n is an integer 
variable?

34b.

35a. What are all possible results of the expression (n % m), where n and m are integer variables?

35b.

36a. Challenge exercise Change the clock from a 24-hour clock to a 12-hour clock. 
Be careful: This is not as easy as it might at first seem. In a 12-hour clock, the 
hours after midnight and after noon are not shown as 00:30, but as 12:30. Thus, 
the minute display shows values from 0 to 59, while the hour display shows values from 
1 to 12!

36b.

37a. There are (at least) two ways in which you can make a 12-hour clock. One 
possibility is to just store hour values from 1 to 12. On the other hand, you can 
simply leave the clock to work internally as a 24-hour clock but change the display 
string of the clock display to show 4:23 or 4.23pm when the internal value 
is 16:23. Implement both versions. Which option is easier? Which is better? Why?

37b.
