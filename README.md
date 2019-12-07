# Introduction to Ruby

![](images/ruby.gif)

## Lesson Objectives

- [Installing Ruby](install-ruby.md)
- [Running your Ruby Scripts](how-to-run-ruby.md)
- Compare/contrast Ruby and JavaScript as programming languages
- Identify specific differences between Ruby and JavaScript in the following areas...
  - Variables
  - Fundamental Data Types
  - Data Collections
  - Conditionals
  - Data Immutability
- Explain and apply Ranges
- Interact with symbols and explain their significance

## Introduction

![](images/rubys-not-a-girl.jpg)

Ruby is a server-side language. It was designed and developed in 1995 by [Yukihiro "Matz" Matsumoto](https://en.wikipedia.org/wiki/Yukihiro_Matsumoto) in Japan.

His philosophy in building Ruby was not about simplicity, but making programming in Ruby feel natural in a way that mirrors life.

This brought about a motto that is common among the Ruby community.

> "Matz Is Nice And So We Are Nice"

> "Programmers often feel joy when they can concentrate on the creative side of programming, so Ruby is designed to make programmers happy." — Yukihiro "Matz" Matsumoto

Performing everyday tasks, while intricate and complex, come to you naturally.

> "Ruby is simple in appearance, but is very complex inside, just like our human body." — Yukihiro "Matz" Matsumoto

## Learning a New Language

If you were going to learn a new programming language, what questions would you have? <br><br>
You've already learned one programming language, and you're about to learn another! <br><br>
Think about the things you now know how to do in JavaScript. With this knowledge, consider what you might want to know about Ruby. 

<br><br>
Take a few minutes to think about some questions that you have about this new language.

Examples:

- How do I define a variable in Ruby? Is it different than in JavaScript?
- Where do I go for information about Ruby? What kind of documentation exists for it?
- Does Ruby have functions?

Ruby and JavaScript each have unique features that you may find useful. At the end of the day, you'll find that they share many qualities.

#### Flexibility

Ruby is flexible making it ideal for coding. What this means is that there are no* blackboxes in Ruby. You can open up anything and change it. This could be a powerful tool in the hands of a skilled Rubyist.

#### Readability

Ruby is hyper readable, the lack of `;`, `()`, keywords like `var`, `let`, `const`, `return`, `function` mean that your semantic naming of methods and variables combined with the semantic nature of the core library methods result in code that feels more like English than a programming language.

![](images/pair.jpg)

**Read the following aloud to yourself.**

```ruby
5.times { print "Hello!" }
```
<br>

#### LAB: (5 mins)

What the difference between p, puts and print.
<br>
<br>
p and puts concatenating "\n" in every iteration. <br>
While print prints all statements in one line. <br>
<br>
And p is also returning each string in double quotes as well. <br>

<br><br>


```ruby
['toast', 'cheese', 'cola'].each { |food| print food.capitalize  }
```

```ruby
  number = 3
  # => 3

  if( number == 3 ) # with parens
    puts( "It's a 3!" )  
  end  
  # It's a 3!
  # => nil

  if number == 3 # without parens
    puts "It's a 3!"  
  end  
  # It's a 3!
  # => nil
```

#### Frameworks

We're going to spend most of our time with Ruby learning Ruby on Rails. It's a application framework for Ruby similar to Express but 10x more robust.

## Ruby Basics

### Variables

We no longer need to precede new variables with `let` or `const`. Just use the name of the variable!

* Variables are instantiated as they are used
* Written in snake_case. That means all lower case with words separated by underscores.
* Variable names should still be semantic (relating to meaning in language or logic).
* Variables are still assigned using a single equals sign ( = )


```ruby
my_favorite_animal = "flying squirrel"
# => "flying squirrel"
```

### Global Variables
Although we don't use `let` or `const`, there is still syntax to designate whether a variable is local or global.<br>

Global variables begin with $. Uninitialized global variables have the value nil and produce warnings. <br>

Assignment to global variables alters the global status. <br>

Here is an example showing the usage of global variable. <br>

```ruby
$global_variable = 10
class Class1
   def print_global
      puts "Global variable in Class1 is #$global_variable"
   end
end
class Class2
   def print_global
      puts "Global variable in Class2 is #$global_variable"
   end
end

class1obj = Class1.new
class1obj.print_global
class2obj = Class2.new
class2obj.print_global
```

### Instance Variables
Instance variables begin with @. Uninitialized instance variables have the value nil and produce warnings.

Here is an example showing the usage of Instance Variables.

```ruby
#!/usr/bin/ruby

class Customer
   def initialize(id, name, addr)
      @cust_id = id
      @cust_name = name
      @cust_addr = addr
   end
   def display_details()
      puts "Customer id #@cust_id"
      puts "Customer name #@cust_name"
      puts "Customer address #@cust_addr"
   end
end

# Create Objects
cust1 = Customer.new("1", "John", "Wisdom Apartments, Ludhiya")
cust2 = Customer.new("2", "Poul", "New Empire road, Khandala")

# Call Methods
cust1.display_details()
cust2.display_details()
```

### Local Variables

Local variables begin with a lowercase letter or _. The scope of a local variable ranges from class, module, def, or from a block's opening brace to its close brace {}.

When an uninitialized local variable is referenced, it is interpreted as a call to a method that has no arguments.

In the above example, local variables are id, name and addr.


### puts

puts (short for "put string") is the equivalent of JavaScript's `console.log()`

```ruby
puts "Hello, Ruby!"
# Hello, Ruby!
# => nil
```

### gets

Ruby also allows us to easily accept inputs from the command line using gets

```ruby
user_input = gets
# => "My input\n" (Note that this line was typed by the user in the terminal)

user_input
# => "My input\n"
```
Some notes about gets...

Usually gets is followed by .chomp, which removes the new line generated by the user hitting return. <br>
For Example:
```ruby
name = gets.chomp
puts "Hello #{name}, nice to meet you!"
```

### What’s this chomp business all about?

It’s a Ruby method that changes the results of gets in a very specific way. <br>

Try removing it. Including the dot (.) before it, so it becomes name = gets, instead of name = gets.chomp. <br>

If you save your code & run it again… <br>

You’ll see that your greeting is now broken down into two lines, instead of the whole greeting being in one line. <br>

##### AND

If you need to convert your value to a number, add `.to_i` to the end of the method

Let's test gets by using it in a Ruby file...

```ruby
# Run this code in app.rb

# Asks for and stores a command line input into the variable as a string.
puts "How old are you?: "

user_input = gets.chomp.to_i

if user_input > 10
  puts "You are older than ten"
end

# In the terminal from in the same directory as app.rb

$ ruby app.rb
# => How old are you?:
20
# => You are older than ten

$ ruby app.rb
# => How old are you?:
```


## Data Types

### Everything Is An Object!

Everything in Ruby is an **object**.

* By "object" we mean that everything has its own set of properties and methods
* Not a new concept. Some data types in JavaScript had their own properties and methods (e.g., `string.length`)
* You will learn more about this when you dive into Ruby OOP

### Numbers

Ruby uses same arithmetic operators as JavaScript:

* `+`, `-`, `*`, `/`, `%`
* Same order of operations too: P.E.M.D.A.S.  <br>
It stands for Parentheses, Exponents, Multiplication/Division, Addition/Subtraction

```rb
1 + 2 # Addition
# => 3

6 - 5 # Subtraction
# => 1

5 * 2 # Multiplication
# => 10

30 / 5 # Division
# => 6

31 / 5 # Note: integer division
# => 6

30 % 5 # Modulo (remainder)
# => 0

31 % 5
# => 1

3 ** 2 # Exponentiation
# => 9
```

Examples:

```ruby
p 0.1
p 42
p 124971240712
p 1_234_567
```

Underscores are ignored in Ruby numbers. Making them useful for readability.

### Strings

Words, just like in JavaScript.

* Surrounded by single or double-quotes
* Ruby uses similar escape characters
  - [Here is a list of them](http://www.java2s.com/Code/Ruby/String/EscapeCharacterslist.htm)
  - Must instantiate string with double-quotes for escape characters to work

```rb
name = "John"
# => "John"

full_name = "John\nDoe"
# => "John\nDoe"

single_quote = 'John\nDoe'
# => "John\nDoe"

puts full_name
# John
# Doe
# => nil

puts single_quote
# John\nDoe
# => nil
```

Not only can you concatenate strings, now you can multiply them too! Remember we couldn't do that in JavaScript?

```rb
# Concatenation
"Hello " + "there!"
# => "Hello there!"

# Multiplication
"Hello there! " * 3
# => "Hello there! Hello there! Hello there! "
```

You can concatenate strings but this is NOT recommend.

```ruby
'foo' + 'bar' # => 'foobar'
'foo' + 2 # => TypeError: no implicit conversion of Integer into String
'foo' + 2.to_s # => 'foo2'
```


Use single quotes for strings that are not interpolated.


#### String Interpolation

Sometimes you will want to print out a string that incorporates a variable. For example...

```rb
my_name = "Jim"
# => "Jim"

puts "Hi my name is: " + my_name
# Hi my name is: Jim
# => nil
```

This works fine. Things aren't so simple when that variable is of a different data type. Like a number...

```rb
class_number = 984
# => 984

puts "I am teaching SEI " + class_number
# TypeError: no implicit conversion of Fixnum into String from (pry):26:in `+'
```

In cases like the above, you either need to convert the variable to a string using `.to_s` or use something called "interpolation."

* Surround the non-string variable with a hashtag and curly brackets: `#{variable}`. **If you choose this option, you must use double quotes otherwise the interpolation will not work.**
* No JavaScript equivalent [(until ES6 came along)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

```rb
class_number = 42
# => 42

puts "I am teaching SEI #{class_number}"
# I am teaching SEI 42
# => nil
```

### Booleans

Still `true` and `false`.

* We'll be using them in conditionals and comparisons just like in JavaScript

Comparison operators in Ruby are nearly identical to JavaScript. However, the check for equality is always for both **value** and **data type**.
* `<`, `>`, `<=`, `>=`, `==`, `!=`

> Don't worry about `===` in Ruby for now. It [does not](http://mauricio.github.io/2011/05/30/ruby-basics-equality-operators-ruby.html) have the same application as in JavaScript.


### ”===” - triple equals

```ruby
if 1..18 === age
  puts 'just out of college'
elsif 19..30 === age
  puts 'wild years'
elsif 31..40 === age
  puts 'i better find a job in a big corp'
else
  puts 'retirement plan'
end
```

<br><br>

But... the more better way to write the above code snippet is:

<br>

```ruby
age = 19

case age
  when 1..18
    puts 'just out of college'
  when 19..30
    puts 'wild years'
  when 31..40
    puts 'i better find a job in a big corp'
  else
    puts 'retirement plan'
end
```

Logical operators are also similar.

* `!`, `&&`, `||`

"Truthiness" and "falsiness" are a lot less complicated in Ruby.

* The only falsey values in Ruby are `nil` and `false`

### Nil

Ruby's "nothing".

* The equivalent of JavaScript's `null`
* You will usually see it when something does not have a return value (e.g., a `puts` statement)
* Like in JavaScript, `nil` is falsey

Need to check if something is `nil`? Use `.nil?`

> **NOTE:** Any method that ends with a `?` means it will return a boolean value.  

```rb
something = "A thing"
# => "A thing"

something.nil?
# => false

something = nil
# => nil

something.nil?
# => true
```

### Operators

You’ll use the following list of operators to do math in Ruby or to compare things. Scan over the list, recognize a few. You know, addition + and subtraction - and so on.

```
** !  ~  *  /  %  +  -  &
<< >> |  ^  >  >= <  <= <=>
|| != =~ !~ && += -= == ===
.. ... not and or
```

### Conditionals

Pretty similar to JavaScript, with some differences.

- No parentheses or curly brackets required
- Begin blocks using if, elsif (no second "e"!) and else
- We close the whole loop using end
    - This will be used throughout Ruby when dealing with code blocks (e.g., method/function)

Here's an example where we check for height at a roller coaster...

```ruby
puts "Welcome to the Iron Rattler! How tall are you (in feet)?"
height = gets.chomp.to_i

if height < 4
  puts "Sorry, you'll fly out of your seat if we let you on."
elsif height < 7
  puts "All aboard!"
else
  puts "If you value your head, you should not get on this ride."
end
```

#### `if` / `unless`
We also have single-line ifs

```ruby
puts 'you are old!' if age >= 100
```

You may even see `unless`

```ruby
puts 'you are old!' unless age < 100
```
When you see an `unless foo`, read it as `if !foo`

> `if !foo` can always be written as `unless foo` which creates a more readable line


#### Ternary operator  

A ternary operator looks just like we have seen in JS `condition ? true : false`

```ruby
1 > 2 ? x = "condition is true" : x = "condition is false"
p x
```

A more real life example is:

```ruby
num = 8
num.even? ? x = "#{num} is even!" : x = "#{num} is odd!"
p x
```

Same as:

```ruby
if num.even?
  "#{num} is even!"
else
  "#{num} is odd!"
end
```

#### Case statement

The case statement in Ruby, can be seen as a shorthand for a series of `if` statements. Unlike other languages, there is no fallthrough. Only the first matching case will be executed.

Example:

```ruby
num_of_wheels = 1

case num_of_wheels
when 1
  p "Unicycle"
when 2
  p "Bicycle"
when 4
  p "Car"
else
  p "I'm not sure"
end
```

Let's redo the roller coaster example from before where we check for height using the case statement this time.

```ruby
puts "Welcome to the Iron Rattler! How tall are you (in feet)?"
height = gets.chomp.to_i

case
when height < 4
  puts "Sorry, you'll fly out of your seat if we let you on."
when height < 7
  puts "All aboard!"
else
  puts "If you value your head, you should not get on this ride."
end
```

##### A More Compact Syntax

There are times when there are a large number of small `when` clauses. Such a case statement easily grows too large to fit on the screen. When this is the case (no pun intended), you can use the `then` keyword to put the body of the `when` clause on the same line.

While this makes for some very dense code, as long as each when clause is very similar, it actually becomes more readable.

When you should use single-line and multi-line when clauses are up to you, it's a matter of style. However, mixing the two is not recommended - a case statement should follow a pattern to be as readable as possible.

Example:

```ruby
person_name = "Saad"

case person_name
when "Saad" then p "Lead Instructor"
when "Abdullah" then p "IA"
else
  p "Student"
end
```

### The Bang Symbol (!)

All of the Ruby data types we have discussed so far are mutable.

We can not only change what variables are pointing to in memory, but we can directly modify those values stored in memory as well.
Methods with an `!` attached to the end of them usually mean that they will modify the value in memory they are being called on.

```ruby
a = "cheeseburger"
# => "cheeseburger"

a.upcase
# => "CHEESEBURGER"

a
# => "cheeseburger"

a.upcase!
# => "CHEESEBURGER"

a
# => "CHEESEBURGER"
```

Things can get tricky when you have multiple variables pointing at the same value. For example...

```ruby
a = "cheeseburger"
# => "cheeseburger"

b = a
# => "cheeseburger"

b.upcase!
# => "CHEESEBURGER"

a
# => "CHEESEBURGER"
```

### Symbols

Symbols are immutable, constant values. That means they contain the same value through the entirety of a program and cannot be changed.

- Kind of like a string that never changes
- Syntax: variable_name = :symbol_name
- No JavaScript equivalent (until ES6 came along!))

```ruby
favorite_animal = :dog
# => :dog

favorite_animal.upcase!
# NoMethodError: undefined method `upcase!' for :dog:Symbol
# Did you mean?  upcase
```

#### When/why would you use symbols?

* Make sure values that need to be constant stay constant
* Enhance performance, use less memory

Every string you create is unique and takes up space on your computer, even if they're the same value! When we're busy looking up key/value pairs, we don't want to be wasting memory - we want it to be fast!

#### Let's watch:

```ruby 
"Your Name".object_id
#=> a number

"Your Name".object_id
#=> a different number

:your_name.object_id
#=> a number

:your_name.object_id
#=> the same number!
```



## Data Collections

### Arrays

An ordered collection of related values. Same syntax as JavaScript Arrays.

- Square brackets
- Values separated by commas
- Zero-indexed

```ruby
numbers = [1, 2, 3]
# => [1, 2, 3]

animals = ["dog", "cat", "horse"]
# => ["dog", "cat", "horse"]

animals[0]
# => "dog"

animals[1] = "elephant"
# => "elephant"

animals
# => ["dog", "elephant", "horse"]
```

Another super cool Ruby feature is that you can perform arithmetic operations on arrays!

```ruby
numbers = [1, 2, 3]
# => [1, 2, 3]

more_numbers = [4, 5, 6]
# => [4, 5, 6]

lots_of_numbers = numbers + more_numbers
# => [1, 2, 3, 4, 5, 6]

lots_of_numbers - [4, 5, 6]
# => [1, 2, 3]

numbers * 3
# => [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

#### Array Methods

Ruby is very nice. It provides us with an extensive library of array methods we can use to traverse and manipulate arrays.

**IMPORTANT**: You DO NOT need to memorize these. The following is just a sample of array methods available to you. You'll come to be more familiar with these as you need them and look them up in documentation.

#### Push/Pop

These JavaScript methods also exist in Ruby and are used the same way.

```ruby 
numbers = [1, 2, 3, 4, 5]
# => [1, 2, 3, 4, 5]

numbers.push(6)
# => [1, 2, 3, 4, 5, 6]

numbers.push(7, 8, 9)
# => [1, 2, 3, 4, 5, 6, 7, 8, 9]

numbers.pop
# => 9

numbers
# => [1, 2, 3, 4, 5, 6, 7, 8]
```

#### Sort

Organizes array values from lowest to highest. Numbers and strings.
Compare this to how JavaScript handles `sort()`

```ruby
numbers = [3, 1, 5, 2, 4]
# => [3, 1, 5, 2, 4]

numbers.sort
# => [1, 2, 3, 4, 5]
```

#### Delete

- Removes an argument from an array. If there are multiple instances of that argument, it will delete them all
- Look up: .delete_at(), .slice()

```ruby
numbers = [3, 1, 2, 2, 4]
# => [3, 1, 2, 2, 4]

numbers.delete(2)
# => 2

numbers
# => [3, 1, 4]
```

### Hashes

A Ruby hash is an unordered, dictionary-like collection organized by key-value pairs.

`tl;dr A hash is very similar to a JavaScript object.`

```ruby
saad = { name: 'saad', age: 32 }
```

Notice that is looks exactly like a JS object except the keys are symbols, not strings.

```ruby
sei_class = {
  teacher: "saad",  
  students: ["Tony", "Steve", "Bruce"],  
  classroom: 3,
  in_session: true,  
  schedule: {  
    morning: "Ruby Basics",
  }
}  
# => {:teacher=>"saad", :students=>["Tony", "Steve", "Bruce"], :classroom=>3, :in_session=>true, :schedule=>{:morning=>"Ruby Basics"}}
```

Accessing hash values...

```ruby
sei_class[:teacher]
# => "saad"
```
Modifying hash values...

```ruby
sei_class[:teacher] = "Marc"
# => "Marc"
```

You can also use strings as hash keys... 

```ruby
sei_class = {
  "teacher" => "saad",  
  "students" => ["Tony", "Steve", "Bruce"],  
  "classroom" => 3,  
  "in_session" => true,  
  "schedule" => {  
    "morning" => "Ruby Basics",
    "afternoon" => "Enumerables"
  }
}  
```
Then can access in this way...

```ruby
sei_class["teacher"]
# => "saad"
```

And modify...
```ruby
sei_class["teacher"] = "Marc"
# => "Marc"
```

**Note the use of => (or "hash rockets") instead of : when using strings as keys.**

#### Hash Methods

Like arrays, Ruby also provides us with a library of hash methods.

 Important Note:
 As mentioned with arrays, do not worry about memorizing these methods. Just know how to look them up should the need arise.

#### Keys

Returns an array with all the keys in a hash.

```ruby
sei_class.keys
# => [:teacher, :students, :classroom, :in_session, :schedule]
```

#### Merge

Combines two hashes. If both of your hashes have the same key, the one in the hash you set as the argument in the parameters will take precedence.

```ruby
classroom = {
 room: 1  
}  
# => {:room=>1}

locations = {
 location_one: "DC",  
 location_two: "NY",  
 location_three: "Riyadh"  
}  
# => {:location_one=>"DC", :location_two=>"NY", :location_three=>"Riyadh"}

silly_hash = classroom.merge(locations)
# => {:room=>1, :location_one=>"DC", :location_two=>"NY", :location_three=>"Riyadh"}

classroom
# => {:room=>1}

locations
# => {:location_one=>"DC", :location_two=>"NY", :location_three=>"Riyadh"}

silly_hash
# => {:room=>1, :location_one=>"DC", :location_two=>"NY", :location_three=>"Riyadh"}
```

#### Ranges

Use ranges to quickly generate arrays of data types.

Parentheses Min and max value, separated by two periods. Generate array using .to_a method

```ruby
(1..5).to_a
# => [1, 2, 3, 4, 5]

("a".."z").to_a
# => ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"]
```

Normally, only two dots are used. If a third dot is used, the last value in the range is excluded.

```(0...5)``` represents the numbers 0 through 4.

## Ruby Code Style Guide

The Ruby community is very opinionated about styling. As you are starting out, you MUST follow [these rules](https://github.com/bbatsov/ruby-style-guide).

Here are the most important rules:


**Casing**

* All variables and methods must use `snake_case`
* All classes and modules must use `CamelCase`

# Labs

## Data Type Exercise - Lab

Complete the exercises in [this document](data-types-exercises.md).


## Data Collection Exercise - Lab
Complete the exercises in [this document](data-collections-exercises.md).




## Recommended Material
- [The Ruby documentation for `Array` is a great resource for learning more about these methods](http://ruby-doc.org/core-2.6.1/Array.html).
- [How to Sort Arrays & Hashes in Ruby (Examples Included)](https://www.rubyguides.com/2017/07/ruby-sort/)
- [Again, the Ruby documentation is a great resource](http://ruby-doc.org/core-2.6.1/Hash.html).

