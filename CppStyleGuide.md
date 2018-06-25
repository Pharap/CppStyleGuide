# Pharap's C++ Style Guide

## Use Allman brace style

### Rationale

It's easier to spot matching brace pairs at a glance when braces are vertically aligned.  
The length of the statement header doesn't affect where the opening brace is placed.  
Braces stand out better when they're alone on a line.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
int main(void)
{
	const auto integers = std::make_array(3, 5, 7, 9);
	
	int total = 0;
	
	for(size_t i = 0; i < integers.size(); ++i)
	{
		total += integers[i];
		if(integers[i] > 5)
			std::cout << integers[i] << '\n';
	}
	
	std::cout << total;
}
```

**Bad**
```cpp
int main(void) {
	const auto integers = std::make_array(3, 5, 7, 9);
	
	int total = 0;
	
	for(size_t i = 0; i < integers.size(); ++i) {
		total += integers[i];
		if(integers[i] > 5)
			std::cout << integers[i] << '\n';
	}
	
	std::cout << total;
}
```

**Bad**
```cpp
int main(void)
{ const auto integers = std::make_array(3, 5, 7, 9);
	
	int total = 0;
	
	for(size_t i = 0; i < integers.size(); ++i)
	{ total += integers[i];
		if(integers[i] > 5)
			std::cout << integers[i] << '\n';
	}
	
	std::cout << total;
}
```

**Bad**
```cpp
int main(void)
{
	const auto integers = std::make_array(3, 5, 7, 9);
	
	int total = 0;
	
	for(size_t i = 0; i < integers.size(); ++i)
	{
		total += integers[i];
		if(integers[i] > 5)
			std::cout << integers[i] << '\n'; }
	
	std::cout << total; }
```

</details>

## Use tabs for indenting

### Rationale

It takes longer to tap the space bar multiple times than it does to tap the tab key once.  
It takes longer to tap the backspace button multiple times to delete spaces than it does to tap it once to delete a tab.  
(The tab key was actually [invented to solve that issue](https://en.wikipedia.org/wiki/Tab_key#History).)  
Tabs can often be configured to display at different widths,  
thus catering to people who prefer both small indents and people who prefer large indents.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
int main(void)
{
	const auto integers = std::make_array(3, 5, 7, 9);
	
	int total = 0;
	
	for(size_t i = 0; i < integers.size(); ++i)
	{
		total += integers[i];
		if(integers[i] > 5)
			std::cout << integers[i] << '\n';
	}
	
	std::cout << total;
}
```

**Bad**
```cpp
int main(void)
{
    const auto integers = std::make_array(3, 5, 7, 9);
    
    int total = 0;
    
    for(size_t i = 0; i < integers.size(); ++i)
    {
        total += integers[i];
        if(integers[i] > 5)
            std::cout << integers[i] << '\n';
    }
    
    std::cout << total;
}
```


**Bad**
```cpp
int main(void)
{
  const auto integers = std::make_array(3, 5, 7, 9);
  
  int total = 0;
  
  for(size_t i = 0; i < integers.size(); ++i)
  {
    total += integers[i];
    if(integers[i] > 5)
      std::cout << integers[i] << '\n';
  }
  
  std::cout << total;
}
```

</details>

## Do not put spaces before brackets

### Rationale

Keywords can be differentiated from functions via syntax highlighting,  
thus placing an extra space between keywords such as `if`, `for` and `while` and the brackets that follow provides no additional benefit.  
Having a space before the bracket also gives the appearance that the contents of the brackets are being kept disjoint from the keywords for some reason, which can be misleading.  
Furthermore, the appearance of a space before brackets after keywords can be quite visually jarring when juxtaposed with function calls that have no spaces before the brackets.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
for(int i = 0; i < 10; ++i)
	if((i % 2) == 0)
		std::cout << i << '\n';
```

**Bad**
```cpp
for (int i = 0; i < 10; ++i)
	if ((i % 2) == 0)
		std::cout << i << '\n';
```

</details>

## Put comments above a line

### Rationale

Lines of code can sometimes be quite long, which can lead to comments being cut off.  
Comments above a statement are easier to spot when skim-reading.  
Comments above a statement can span several lines.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
// Print all even numbers between 0 to 9 inclusive
for(int i = 0; i < 10; ++i)
	if((i % 2) == 0)
		std::cout << i << '\n';
```

**Bad**
```cpp
for (int i = 0; i < 10; ++i) // Print all even numbers between 0 to 9 inclusive
	if ((i % 2) == 0)
		std::cout << i << '\n';
```

</details>

## No more than one assignment per line

### Rationale

Having multiple assignments per line forces the programmer to stop and think about the order of assignment.  
By having just one assignment per line, assignments become more obvious and can be understood at a glance.  

<details>
<summary><strong>Examples<strong></summary>

**Bad**
```cpp
red = green = blue = 0;
```

**Good**
```cpp
red = 0;
green = 0;
blue = 0;
```

</details>

## No more than one statement per line

### Rationale

Having multiple statements per line makes it harder to skim-read code because a programmer must stop and read every statement on the line.  
By having just one statement per line, it's easier to skim-read code and code reads as if it were a clear list of instructions.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
const int value = array[i];
++i;
```

**Bad**
```cpp
const int value = array[i++];
```

**Good**
```cpp
++i;
++j;
const int value = i + j;
```

**Bad**
```cpp
const int value = ++i + ++j;
```

</details>

## No more than one variable definition per line

### Rationale

Having multiple variable definitions makes it harder to skim-read code because a programmer must stop and read every variable on the line.  
By having just one variable definition per line, the variables are clearly listed along with their type so it's harder to miss a variable or type when skim-reading code.  
Having multiple variable definitions per line can also cause confusion when it comes to defining pointers and references.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
int value = 0;
int * pointer = &value;
int & reference = value;
```

**Bad**
```cpp
int value = 0, * pointer = &value, & reference = value
```

**Bad**
```cpp
int value = 0, *pointer = &value, &reference = value
```

</details>

## Leave spaces around the pointer symbol when defining pointer variables

### Rationale

Some people like to think of the pointer as part of the type because pointers are considered to be types in most contexts.  
Some people like to think of the pointer as part of the variable because of the strange rule when declaring more than one variable per line.  
This is an example of C++'s constext sensitivity.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
int value = 0;
int * pointer = &value;
```

**Bad**
```cpp
int value = 0;
int* pointer = &value;
```

**Bad**
```cpp
int value = 0;
int *pointer = &value;
```

</details>

## Leave spaces around the reference symbol when defining reference variables

### Rationale

Some people like to think of the reference as part of the type because references are considered to be types in most contexts.  
Some people like to think of the reference as part of the variable because of the strange rule when declaring more than one variable per line.  
This is an example of C++'s constext sensitivity.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
int value = 0;
int & reference = value;
```

**Bad**
```cpp
int value = 0;
int& reference = value;
```

**Bad**
```cpp
int value = 0;
int &reference = value;
```

</details>

## Leave spaces around binary operators

### Rationale

The `->` and `.` operators are explicitly exempt from this rule due to their special role.

Leaving spaces around operators makes the presence of the operators easier to spot and makes it easy to discern binary operators from unary operators.  
(i.e. a bitwise and cannot be mistaken for taking the address of a variable,  
a subtraction cannot be mistaken for a negation and a multiplication cannot be mistaken for a pointer dereference.)  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
float magnitude = std::sqrt((x * x) + (y * y));
float xNormal = x / magnitude;
float yNormal = y / magnitude;
```

**Bad**
```cpp
int magnitude = std::sqrt((x*x)+(y*y));
float xNormal = x/magnitude;
float yNormal = y/magnitude;
```

</details>

## Use preincrement and predecrement, avoid postincrement and postdecrement

### Rationale

Increment and decrement are mutating operations - they alter the value of an lvalue expression.  
By putting the mutating operation earlier, it becomes more obvious.  

Additionally, it avoids generating an implicit copy of a value.  
Good compilers will optimise away the copy, but that optimisation is not performed and sometimes not even possible.  

Lastly, C++'s concept of iterators specifies the expression `++iterator` but not the expression `iterator++`,  
i.e. iterators are not required to implement postincrement but are required to implement preincrement.  
The concept of input iterators specifies that the expression `*iterator++` must be valid, but defines it in terms of `++iterator`,  
whilst it makes no mention of the validity of `iterator++` other than `(void)iterator++` must be valid and equivalent to `(void)++iterator`.

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
// Mutating operation is given precidence
for(size_t i = 0; i < array.size(); ++i)
	++array[i];
```

**Bad**
```cpp
// Mutating operation is at the end of the line
for(size_t i = 0; i < array.size(); i++)
	array[i]++;
```

## Don't use C style casts

### Rationale

When using C style casts it is possible to accidentally cast away a `const` qualifier without intending to,  
which can change the semantics of the code.  
When using C++ style casts, one would have to explicitly use `const_cast` to remove a `const` qualifier,  
thus it's much harder to remove by accident.  

When using C style casts it is possible to make unintended type conversions,  
for example converting an `int *` to a `float *`.  
When using C++ style casts, `static_cast` will forbid this conversion at compile time, whilst `reinterpret_cast` will allow it,  
hence C++ style casts give a greater indication of whether a conversion was actually intended as well as signalling a relative degree of danger.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
// TBC
```

</details>

## Be explicit with casting

### Rationale

Many implicit conversions can lead to hard to hard to spot bugs.  
Implict conversion between signed and unsigned types is one of the most notable of these.  
Using explicit casts makes the conversion easier to spot and makes it clear that the type conversion was intentional.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
// Intent is clear
std::int8_t a = -5;
std::uint8_t b = static_cast<uint8_t>(a);
```

**Bad**
```cpp
// Was the author aware that they're converting a negative?
std::int8_t a = -5;
std::uint8_t b = a;
```

</details>

</details>

## Use `size_t` for indices, not `int`

### Rationale

`size_t` is the canonical type for dealing with memory indexing.  
On certain processors, unsigned numbers perform better.  

Note that there are some cases where using `size_t` instead of `int` can introduce bugs,  
such as interating backwards and forgetting to check if a collection type is empty.  

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
// No warnings, no errors
for(size_t i = 0; i < array.size(); ++i)
	array[i] += 2;
```

**Bad**
```cpp
// Fails if `array.size() > std::numeric_limits<int>::max`.
// Produces warning about comparing signed with unsigned.
for(int i = 0; i < array.size(); ++i)
	array[i] += 2;
```

</details>

</details>

## Prefer `'\n'` over `std::endl` when using `std::cout`

### Rationale

Many people don't realise that `std::endl` actually flushes `std::cout`'s internal buffers,  
which can have a big negative impace on performance.
Hence it's better to use `'\n'`, unless flushing is desired,
e.g. if the line needs to be shown immediately or it is the last line.

<details>
<summary><strong>Examples<strong></summary>

**Good**
```cpp
// Queue array.size() lines
for(size_t i = 0; i < array.size(); ++i)
	std::cout << i << ' ' << array[i] << '\n';
	
// Perform one flush
std::cout << std::flush;
```

**Bad**
```cpp
// Flush the output with every single item
for(size_t i = 0; i < array.size(); ++i)
	std::cout << i << ' ' << array[i] << std::endl;
```

</details>

