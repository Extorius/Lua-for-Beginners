# Lua-for-Beginners
Essentially an explanation of the basics of Lua, such as tables, functions, strings, variables, etc.

## 1. - Variables
Variables are what you use to store data. You can think of a variable as a piece of data that you put down, and you can pick it up and use it later.
There are two types of variables:
- Local
- Global

Essentially, a global variable can be called anywhere from any thread (useful for functions and threadings), but sometimes you want to refresh a variable without getting rid of its original value. This is where local variables come into place.
A local variable will define a value that's unique to its thread; meaning you can have multiple variables in different threads, with the same name but different values.

Here's an example of global and local variables:
```lua
-- local variable
local v = 1
print(v) -- should print 1 as an integer

local function f() -- defining the function
    print(v) -- should error, as the 'v' variable was defined in a different thread, thus doesn't exist in this one
end

f() -- calling the function
```
```lua
-- global variable
v = 1
print(v) -- should print 1 as an integer

local function f() -- defining the function
    print(v) -- should hopefully also print 1 as an integer, since the variable was defined as a global variable; and thus can be called by any thread
end

f() -- calling the function
```

## 2. - Functions
Functions allow you to essentially store code the same way you would store a string, integer, or table in a variable. This is useful to get rid of repetitive code or reduce having to copy and paste code that does the same thing.
Variables called in functions are unique to that thread. So, if you define a local variable outside of a function and then call on it inside of that function, it will equal nil as it has not been defined in that thread. The same goes for defining a local variable inside of a function and calling it outside of that function.
Global variables in functions are entirely different, and would likely work a lot more like how you expect. If you define a global variable outside of a function and call it inside that function, it will work and it will not equal nil. The same goes for defining a global variable inside of a function and calling it outside of that function.

```lua
local function Add(number1, number2) -- here, we define two parameters that will be used inside of the function. This is a good way to store local variables outside of a function, and still have the function be able to call on them.
    return number1 + number2 -- the usage of return allows this function to essentially act as a variable that can return a value based on the information it's fed
end

print(Add(1, 2)) -- here, we call the function we defined above and pass the two parameters: number1, and number2. Now, since we used return in the function it will be interpreted as 3 (since 1 + 2 == 3).
```

## 3. - Strings, Integers, Tables, and Booleans
In Lua, there are 3 main types of data: Strings, Integers, and Tables. Each has its own purpose and is what you'll be using in almost all your lines of code, in one way or another.

- Strings:
Everything I have written so far can be defined as a string: Text, essentially. It doesn't matter if the text contains UPPERCASE LETTERS LIKE THIS, or lower case letters like this, 0r numb3r6 l1k3 th15. It will all be interpreted as a string, as long as you specifically tell Lua how to interpret it.

- Integers:
Integers are a lot easier to understand. They're numbers. Formulas, mathematical equations, and more will be interpreted as an integer by Lua. This is why you can do something like print(1+2) and it won't literally print '1+2', but instead 3.

- Tables:
Tables are by far the most complicated and will take a while to master. Essentially, you can think of tables as all 3 of these in the same variable. You can store strings, integers, and other tables in a table, and access it. This is especially useful for more complicated code and will make life a lot easier, and minimize the use of defining variables.

- Booleans:
You can think of a boolean as a true or false, or a 1 or 0. A boolean will always be one of two values and will most commonly be used in conditions.

Here's an example of how to use all 4:
```lua
-- strings
local v1 = 'Hello'
local v2 = ' '
local v3 = "world!"

print(v1 .. v2 .. v3) -- this will print 'Hello world!'. By using double periods, we tell Lua to add to the string it's printing. So, if we did something like print(v1 .. v3) instead, it would look more like 'Helloworld!'
print(v1,v3) -- by using a comma instead of .., Lua will add the space for us. This can also be used to print both integers and strings at the same time.
```
```lua
-- integers
local v1 = 1 -- 1
local v2 = 1 + 1 -- 2
local v3 = v1 + v2 -- 3

print(v1, v2, v3) -- prints 1, 2 ,3 in that order. Since these are integers, you don't need to wrap them in quotation marks.
```
```lua
-- tables
local v1 = 1 -- 1
local v2 = 'Hello world!' -- 'Hello world!'
local v3 = {v1, v2} -- A table containing both 1 and 'Hello world!'

print(v1) -- prints 1
print(v2) -- prints 'Hello world!'
print(v3) -- prints.. nothing. That's because you can't print tables in Lua, only the values stored in it.

print(v3[1]) -- prints 1. This is because the first value stored in the table is equal to 1; So by calling v3[1] we're essentially just asking for the first value in that table.
print(v3['Hello world!']) -- prints.. Well, nothing. This would cause an error, as there is no Hello world!st value in the table. Essentially, you don't 'index' (searching through a table for a specific spot) a table by searching for the value, you search for the spot where the value is stored.
print(v3[2]) -- prints 'Hello world!', because we correctly searched for the spot, not the value.
```
```lua
-- booleans
local v1 = true
local v2 = 'Hello world!'
local v3 = 'Goodbye world!'

if v1 == true then -- this is an example of a basic condition, that will check if v1 equals true.
    print(v2) -- if v1 does equal to true, then print 'Hello world!'.
else
    print(v3) -- if v1 does not equal true, then print 'Goodbye world!'.
end
```

## 4. - Conditions & if Statements
Now that you have the absolute basics sorted out, you can move on to some of the most headache incuding part of learning programming: Conditions & if statements.
Essentially, imagine you have two values. One is a boolean, the other is a string. Now, if you want to check if the first value equals true to print the second value, you can use a condition.

Conditions can be used for many different things:
- If statements
- Loops
- Defining values
- And a few other things

Here's an example of how you can use a condition to do all of the above:
```lua
-- if statement

local v1 = true
local v2 = 'Hello world!'

if v1 == true then -- checks if our boolean, v1, is equal to true.
    print(v2) -- if it does, we print our string, v2, which is equal to 'Hello world!'.
end
```
```lua
-- loops

local v1 = true
local v2 = 1

while v1 == true do -- here, we define a loop that will always run while v1 is equal to true
    v2 = v2 + 1 -- here, we add 1 to v2 by saying that v2 is equal to itself plus 1
    
    if task then -- here, we check if the task library exists (for Roblox Lua)
        task.wait() -- and if it does exist we wait to avoid crashing Roblox Lua users
    end
end
```
```lua
-- defining values

local v1 = true
local v2 = (v1 == true and 1) or (v1 == false and 0) -- here, we check if v1 equals to true, and if it does we make v2 equal to 1. By using or, we pretty much say that if v1 doesn't equal true, try something else; which in this case is checking if it equals 0 and if so make v2 equal 0.
local v3 = not v1 -- here, we say that v3 is equal to not v1, or pretty much the exact opposite, which is false.

print(v2) -- prints 1
print(v3) -- prints false
```

## Quizzes
### Level 1: Print
Write a program that prints 'Hello world!'
* Hint: You can use the built-in `print` function in Lua, and pass the string 'Hello world!' as the first parameter

#### Answer
Look away if you don't want the answer to be spoiled!

<details><summary>Show Answer</summary><pre><code>-- Note: There is other ways of doing this, and no one way is correct. If it works, it works.
print('Hello world!')
</code></pre></details>

### Level 2: Variables
Write a program that stores a variable equal to 'Hello world!', and then prints it
* Hint: You can use the denonimator `local` to define a variable

#### Answer
Look away if you don't want the answer to be spoiled!

<details><summary>Show Answer</summary><pre><code>-- Note: There is other ways of doing this, and no one way is correct. If it works, it works.
local v1 = 'Hello world!'
print(v1)
</code></pre></details>

### Level 3: Functions
Write a program that defines a function that accepts two parameters, and returns the first parameter plus the second parameter
* Hint: You can use the denominator `return` to return a value from a function

#### Answer
Look away if you don't want the answer to be spoiled!

<details><summary>Show Answer</summary><pre><code>-- Note: There is other ways of doing this, and no one way is correct. If it works, it works.
local function Add(number1, number2)
    return number1 + number2
end

print(Add(1, 2))
</code></pre></details>
