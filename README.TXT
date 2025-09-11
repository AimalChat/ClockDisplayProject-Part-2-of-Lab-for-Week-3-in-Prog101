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

21b."00:00", because that is the set initial value for the object when initiallized.

22a. Open an inspector for this object. With the inspector open, call the object’s 
methods. Watch the displayString field in the inspector. Read the project comment 
(by double-clicking the text icon in the class diagram) for more information.

22b

23a. How many times would you need to call the timeTick method on a newly created 
ClockDisplay object to make its time reach 01:00? How else could you make it display 
that time?

23b.I would have to call the timeTick method 60 times in order to reach the desired
"01:00" String display. Alternatively, you may call the setTime method and write in the
respectve parameters : 1 for hours and 0 for minutes.

24a. Write down the definition of a variable of type NumberDisplay called digit. 
Write an assignment statement that creates a NumberDisplay object with a rollover 
limit of 10 and assigns the object to the variable.

24b.private NumberDisplay digit; 
& 
private NumberDisplay digit;
digit = new NumberDisplay(10);

25a. Write Java statements that define a variable named window of type Rectangle, 
and then create a rectangle object and assign it to that variable. The rectangle 
constructor has two int parameters for the lengths of its sides.

25b.
ex: 
public class Drawing
{
private int lengtH;
private int width;
...

public createWindow()
{
private Rectangle window;
window = new Rectangle(length, width);
}
...
}
26a. Look at the second constructor in ClockDisplay’s source code. Explain what it 
does and how it does it.

26b.It allows the user to create a ClockDisplay object with a specified number
displayed/ String displayed by inputting int values that initialize both hours
and minutes.

27a. Identify the similarities and differences between the two constructors. 
Why is there no call to updateDisplay in the second constructor, for instance?

27b.First, the similarities are that both create two objects of type NumberDisplay 
named hours and miuntes that have their own respective limits or rollover limits
, 24 for hours and 60 for minutes. As for the differences, the ClockDisplay() 
constructor has no formal parameters as opposed to the ClockDisplay(int hour, int minute)
constructor that has two int type parameters. Another one is the last lines of code for
the both. First one having : "updateDisplay();" while the second one has : 
"setTime(hour, minute);". As for why there is a discrpency in the second constructor,
it is due to the inputted values necessary to customize the String returned to the user.
We shouldnt updateDisplay because there is no need for it, we set the time with the 
received pieces of data. ****

28a. Given a variable
 Printer p1;
which currently holds a reference to a printer object, and two methods inside 
the Printer class with the headers.
 public void print(String filename, boolean doubleSided)
 public int getStatus(int delay)
write two possible calls to each of these methods.

28b. p1.print("Sales.jpeg", true);
p1.print("001.png", false);
&
p1.getStatus(100);
p1.getStatus(1);

29a. Open the house project from chapter 1 and review the Picture class. What 
types of object are created by the constructor of Picture?

29b.They're all class objects.

30a. List all the external method calls that are made in the draw method of Picture 
on the Triangle object called roof.

30b.
roof.changeSize(60, 180);
roof.moveHorizontal(20);
roof.moveVertical(-60);
roof.makeVisible();

31a. Does the Picture class contain any internal method calls?

31b.No, I dont think so since all methods definied in this class werent repeated in
any of the method bodies.

32a. What is the result of the expression (8 % 3)? In other words, what value 
remains when 8 is divided by 3?

32b.2

33a. Try out the expression (8 % 3) in the Code Pad. Try other numbers. What happens 
when you use the modulo operator with negative numbers?

33b.It gives a negative number if one or both are negative.

34a. What are all possible results of the expression (n % 5), where n is an integer 
variable?

34b. the result of the modulus will always be a remainder between minus infinity and 
4, inclusive. Since the remainder is always smaller than the divisor, meaning it can 
only  or a positive integer value. This means that the result could be 0 to 4,without exceeding 4.

35a. What are all possible results of the expression (n % m), where n and m are 
integer variables?

HELP35b. The result of the modulus will always be an integer between minus infinity and 
m - 1(if m is positive) or m + 1(if m = negative value), and it doesnt depend on whether
n is smaller than m. Because the result always has the same sign as the dividen, meaning, 
by example, 5 % -10 = 5, -5 % 10 = -5.

36a. Challenge exercise Change the clock from a 24-hour clock to a 12-hour clock. 
Be careful: This is not as easy as it might at first seem. In a 12-hour clock, the 
hours after midnight and after noon are not shown as 00:30, but as 12:30. Thus, 
the minute display shows values from 0 to 59, while the hour display shows values from 
1 to 12!

36b.
public class ClockDisplay
{
    private NumberDisplay hours;
    private NumberDisplay minutes;
    private String displayString;    // simulates the actual display
    
    /**
     * Constructor for ClockDisplay objects. This constructor 
     * creates a new clock set at 12:00.
     */
    public ClockDisplay()
    {
        hours = new NumberDisplay(13);
        minutes = new NumberDisplay(60);
        hours.setValue(12);
        updateDisplay();
    }

    /**
     * Constructor for ClockDisplay objects. This constructor
     * creates a new clock set at the time specified by the 
     * parameters.
     */
    public ClockDisplay(int hour, int minute)
    {
        hours = new NumberDisplay(24);
        minutes = new NumberDisplay(60);
        setTime(hour, minute);
    }

    /**
     * This method should get called once every minute - it makes
     * the clock display go one minute forward.
     */
    public void timeTick()
    {
        minutes.increment();
        if(minutes.getValue() == 0) {
            //Increments the hour twice in case of 0 or 12.
            if(hours.getValue() == 0 || hours.getValue() == 12){
                hours.increment();
            }
            // It just rolled over!
            hours.increment();
        }
        updateDisplay();
    }

    /**
     * Set the time of the display to the specified hour and minute.
     */
    public void setTime(int hour, int minute)
    {
        hours.setValue(hour);
        minutes.setValue(minute);
        updateDisplay();
    }

    /**
     * Return the current time of this display in the format HH:MM.
     */
    public String getTime()
    {
        return displayString;
    }
    
    /**
     * Update the internal string that represents the display.
     */
    private void updateDisplay()
    {
        displayString = hours.getDisplayValue() + ":" + 
                        minutes.getDisplayValue();
    }
}

37a. There are (at least) two ways in which you can make a 12-hour clock. One 
possibility is to just store hour values from 1 to 12. On the other hand, you can 
simply leave the clock to work internally as a 24-hour clock but change the display 
string of the clock display to show 4:23 or 4.23pm when the internal value 
is 16:23. Implement both versions. Which option is easier? Which is better? Why?

37b.In my opinion, this one was harder for me to apply. As for which is better, I think
this one may be better since the switch between the 12 and 24 hour cycle is much easier
to do and could even be implemented as a different constructor and such!
    /**
     * Return the current time of this display in the format HH:MM.
     */
    public String getTime()
    {
        /**
         * Create the new display for the 12 hour rotation and replace
         * the original displayed String with this one.
         */
        int hourDisplay = hours.getValue() % 12;
        //No 00:00 for midnight, so if if does equal to 0, change it to 12.
        if(hourDisplay == 0){
            hourDisplay = 12;
        }
        /**
         * Return the fully realized concatination with all the newly
         * added surface level modified hour display.
         */
        displayString = hourDisplay + ":" + minutes.getDisplayValue();
        return displayString;
    }

    /**
     * Return the current time of this display in the format HH:MM.
     */
    public String getTime()
    {
        /**
         * Create the new display for the 12 hour rotation and replace
         * the original displayed String with this one.
         */
        int hourDisplay = hours.getValue() % 12;
        //No 00:00 for midnight, so if if does equal to 0, change it to 12.
        if(hourDisplay == 0){
            hourDisplay = 12;
        }
        //create the additional string for the period of day (am/pm)
        String period;
        //if 0 to 12 = am, else 13 to 24 = pm.
        if (hours.getValue() >= 12){
            period = "pm";
        }
        else{
            period = "am";
        }
        /**
         * Return the fully realized concatination with all the newly
         * added details : period and the surface level modified hour display.
         */
        displayString = hourDisplay + ":" + minutes.getDisplayValue() + period;
        return displayString;
    }
