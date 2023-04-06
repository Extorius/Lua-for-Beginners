# Lua-for-Beginners
Essentially a explanation of the basics of Lua, such as tables, functions, strings, variables, etc.

## 1. - Variables
Variables are what you use to store data. You can think of a variable as a piece of data that you put down, and you can pick up and use later.
There's two types of variables:
1. Local
2. Global

Essentially, a global variable can be called anywhere from any thread (useful for functions and threadings), but sometimes you want to refresh a variable without getting rid of it's original value. This is where local variables come into place.
A local variable will define a value that's unique to it's thread; meaning you can have multiple variables in different threads, with the same name but different values.

Here's an example of global and local variables:
```lua
-- local variable
local v = 1
print(v) -- should print 1 as a integer

local function f() -- defining the function
    print(v) -- should error, as the 'v' variable was defined in a different thread, thus doesn't exist in this one
end

f() -- calling the function
```
```lua
-- global variable
v = 1
print(v) -- should print 1 as a integer

local function f() -- defining the function
    print(v) -- should hopefully also print 1 as a integer, since the variable was defined as a global variable; and thus can be called by any thread
end

f() -- calling the function
```

## 2. - Functions
Functions allow you to essentially store code the same way you would store a string, integer, or table in a variable. This is useful to get rid of repetitive code, or reduce having to copy and paste code that does the same thing.
Variables called in functions are unique to that thread. So, if you define a local variable outside of a function and then call on it inside of that function, it will equal nil as it has not been defined in that thread. Same goes for defining a local variable inside of a function and calling it outside of that function.
Global variables in functions is entirely different, and would likely work a lot more like how you expect. If you define a global variable outside of a function and call it inside that function, it will work and it will not equal nil. Same goes for defining a global variable inside of a function and calling it outside of that function.

```lua
local function Add(number1, number2) -- here, we define two parameters that will be used inside of the function. This is a good way to store local variables outside of a function, and still have the function be able to call on them.
    return number1 + number2 -- the usage of return allows this function to essentially act as a variable that can return a value based on the information it's fed
end

print(Add(1, 2)) -- here, we call the function we defined above and pass the two parameters: number1, and number2. Now, since we used return in the function it will inteperated as 3 (since 1 + 2 == 3).
```

## 3. - Strings, Integers, and Tables
In Lua, there's 3 main types of data: Strings, Integers, and Tables. Each has it's own purpose and is what you'll be using in almost all your lines of code, in one way or another.

Strings:
Everything I have written so far can be defined as a string: Text, essentially. It doesn't matter if the text contains UPPERCASE LETTERS LIKE THIS, or lower case letters like this, 0r numb3r6 l1k3 th15. It will all be inteperated as a string, as long as you specifically tell Lua how to inteperate it.

Integers:
Integers are a lot easier to understand. They're numbers. Formula's, mathematical equations, and more will be inteperated as a integer by Lua. This is why you can do something like print(1+2) and it won't literally print '1+2', but instead 3.

Tables:
Tables are by far the most complicated and will take a while to master. Essentially, you can think of tables as all 3 of these in the same variable. You can store strings, integers, and other tables in a table, and access it. This is especially useful for more complicated code and will make life a lot easier; and minimize the use of defining variables.

Here's an example of how to use all 3:
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
