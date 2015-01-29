## Jacob Fritz Debugger Lab

**Question #1:** Why is `cutoff` not a parameter to the method `playTurn` in the `PigGame` class?

	This is because `cutoff` is a variable within the `PigGame` class, and since `playTurn` is a method in that class, it can access that variable freely.

**Question #2:** What would the following code print?
```
	ScoreSheet s = new ScoreSheet();
	System.out.println(s.getTurnAverage());
```

	It would print "0.0".

**Question #3:** In the `PigGame` class, `numBusts` is incremented in the `playGame` method. Describe how this statement could be moved to another method in the class without affecting the results. 

	It could be moved from the `playGame` method to the `playTurn` method. It could be placed under the if statement, `if (d.getUpValue() == 1)`, after `rolledOne = true;`. This would not affect the results, as currently it checks if `score` equals 0 in the `playGame` method after a turn has been played. This change would simply make the change while the `playTurn` method is running, rather than after it finishes. 

**Question #4:** Based on your current understanding of the code, where do you think the problem(s) might be located? Are there portions of the code where you are fairly certain the problem(s) could not possibly be?

	I would estimate that the logical assumption is that the problem lies in one of the loops running thoughout the program. I do not know if any area can currently be dismissed, although I would say the declaration section and the output sections are unlikely to be incorrect. 

**Question #5:** Describe the problem(s) with the program and the way(s) you made the program execute correctly.

	The problem is that `score` never becomes greater than 0. The score keeps being reset to 0, causing the loop to be run infinitely. This is because when the dice is rolled, the value that is determined, the `upValue`, is always returned as a 1, which then caused the score to be reset, ends the turn, and increases the number of busts. 
	To fix this problem, the code used to convert the random number (`(int)`) needed to be moved outside of the paranthesis, allowing the random number (0.0-0.99) to be multiplied by 6, making it 0.0-5.94, then increased by 1, making it 1.0-6.94. Then, when it is converted to an integer with `(int)`, it will be between 1-6.

	The code now reads `upValue = (int) ((Math.random() * 6) + 1);`.

**Question #6:** Using the correct program, what are the average number of turns for cutoff values 10, 15, 20, and 25?

	Cutoff Value: 10
	Average Number of Turns: 15
	
	Cutoff Value: 15
	Average Number of Turns: 13
	
	Cutoff Value: 20
	Average Number of Turns: 12
	
	Cutoff Value: 25
	Average Number of Turns: 12