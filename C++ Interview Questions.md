<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## C++ Interview Questions







// is used for single line comments.

	```
struct student {
};
	```
You can cast explicitly as follows.

	```
int i, j, k;
	```
void *p;







	* **Destructors** are called when the objects are destroyed.




int func1() {
There are several different types of iterators:  
	&nbsp;&nbsp;&nbsp;input_iterator  
	&nbsp;&nbsp;&nbsp;random_iterator  
	&nbsp;&nbsp;&nbsp;reverse_iterator
	



class shape {
};


A university has people who are affiliated with it. Some are students, some are faculty members, some are administrators, and so on. So a simple inheritance scheme might have different types of people in different roles, all of whom inherit common "Person" class. The Person class could define abstract `getRole()` method which would then be overridden by its subclasses to return the correct role type.  
But now what happens if we want to model a the role of a Teaching Assistant (TA)? Typically, a TA is both a grad student and a faculty member. This yields the classic diamond problem of multiple inheritance and the resulting ambiguity regarding the TA’s `getRole()` method:

	```
// Person
public abstract Role getRole();
// Faculty Member
public Role getRole() {
	return Role.Faculty;
}
// Graduate Student
public Role getRole() {
	return Role.GradStudent;
}
// TA
public Role getRole() {
	return ???
}	
	```

	Which `getRole()` implementation should the TA inherit? The simple answer might be to have the TA class override the `getRole()` method and return a newly-defined role called "TA". But that answer is also imperfect as it would hide the fact that a TA is, in face, both a faculty member and a grad student.

	```
int i = 5;
int j = i++;
	```

	After the above code executes, `i` will equal 6, but `j` will equal 5.  
When the operators unary increment (`++`) and decrement (`--`) precede a variable, the value of the variable is modified first and then the modified value is used. For example, if we modified the above code snippet to insted say `int j = ++i;`, `i` would be incremented to 6 and `j` would be set to that modified value, so both would end up being equal to 6.  
However, when these two operators follow a variable, the unmodified value of the variables is used and then it is incremented or decremented.

	```
cout << 25u - 50;
	```
	
	The answer is not -25. Rather, thw answer is 4294967271, assuming 32 bit integers. Why?  
In C++, if the types of two operands differ from one another, then the operand with the "lower type" will be promoted to the type of the "higher type" operand, using the following type of hierarchy (listed here form highest type to lowest type): long, double, float, unsigned long int, long int, unsigned int, int (lowest).  
So when the two operands are, as in our example, `25u` (unsigned int) and `50` (int), the `50` is promoted to also being an unsigned integer (i.e., `50u`).  
Moreover, the result of the operation will be of the type of the operands. Therefore, the result of the above code will itself be an unsigned integer as well. So the result of `-25` converts to `4294967271` when promoted to being an unsigned integer.

* **What is the error in the code below and how should it be corrected?**  

	```
my_struct_t *bar;
/* ... */
memset(bar, 0, sizeof(bar));
	```
	
	The last argument to `memset` should be `sizeof(*bar)`. `sizeof(bar)` calculates the size of `bar` (i.e., the pointer itself) rather than the size of the structure pointed to by `bar`.  
A sharp candidate might point out that using `*bar` will cause a dereferencing error if `bar` has not been assigned. Therefore an even safer solution would be to use `sizeof(my_struct_t)`.