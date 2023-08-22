**TL;DR: Long methods with more than 10 lines of code are hard to read and maintain. Create new methods for any code that requires comments or explanations, even if it's just a single line. Use descriptive method names to make the code more readable and understandable.**

A method contains too many lines of code. Generally, any method longer than ten lines should make you start asking questions.

Like the Hotel California, something is always being added to a method but nothing is ever taken out. Since it's easier to write code than to read it, this "smell" remains unnoticed until the method turns into an ugly, oversized beast.

Mentally, it's often harder to create a new method than to add to an existing one: "But it's just two lines, there's no use in creating a whole method just for that..." Which means that another line is added and then yet another, giving birth to a tangle of spaghetti code.

## Treatment
As a rule of thumb, if you feel the need to comment on something inside a method, you should take this code and put it in a new method. Even a single line can and should be split off into a separate method, if it requires explanations. And if the method has a descriptive name, nobody will need to look at the code to see what it does.

## Recipe 1: Extract Method
