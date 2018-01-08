# Ruby Methods
### Defining a method
Ruby methods contains a block of code that we can run in order to do some sort of logic.

The way ruby methods are created is:
```
def method_name(arguments_if_any)
    # logic goes here
end
```

example:
```
def add_two_nums(num_1, num_2)
    num_1 + num2
end
```

There are many reasons to create a method:
 - to condense code
 - to have a re-usable method
 - to keep ourselves from repeating logic

### Calling a method
Once we have a method defined, we can then use / call the method:

Going back to our example add_two_nums, we could call this method like this:
```
add_two_nums(1, 3)
```
This would then `return` to us a `value` and this value we can use in our code.

Calling `add_two_nums(1, 3)` will give us `4`. We can use this method in order to do math and other things.

If we were to do:
```
add_two_nums(1, 3) + 4
```
This would give us `8`. What ruby does is sends the value `1` to the placeholder `num_1` where we had defined it, and like a `variable` that automatically sets itself `num_1 = 1`, it will be usuable automatically in our code.

So we send `num_1` the value of `1` and `num_2` the value of `3`. It then adds the two together `num_1 + num_2` and `returns the value`. We then say, we want to take the `value that's returned` and add it to `4` which gives us `8`.

Also something to take note, the last value a method reads is what gets returned. (The last thing read in the method)

Here's an example of a method we can't do that with:
```
def add_two_nums(num_1, num_2)
    puts num_1 + num_2 # this line is the last thing read so the value of puts will be returned
end
```

Puts just logs to the `console` and it's value after it `logs` is `nil`.

So if we tried to do:
```
add_two_nums(1, 3) + 4
```

It would be like saying
```
nil + 4
```
However before it breaks, it would log `4` to the `console`.

### Default arguments

Sometimes we might have a method whose value might have some default value, which also makes that argument optional during the `method call`.

An example would be this:
```
def say(string = "hello world!")
    puts string
end
```
we could then call it two ways:
```
# passing in an argument
say("Goodbye World! (so dramatic)") <= puts out "Goodbye World!"

# without passing in an argument
say <= puts out "hello world!"
```

What happens is when ruby detects no value is being sent to the argument, the argument will automatically set itself to it's default value.

### Common Issues

There are a few rookie mistakes i've seen, here's a few examples:

```
# definition of say
def say(string)
    puts string
end

# calling of say
say
```

When a method is called without `required arguments (meaning no default value for the argument)`. You end up with an `argument error(expected 1, got 0)`. What this is saying is you are calling the method without any arguments `got 0`, and your method `requires` 1 argument `expected 1`.

Here's another example of something you can't do:
```
greeting = "hello"

def say
    # greeting will not be defined here and will throw a undefined method or local variable error
    puts greeting
end

say
```

Also the reverse is true:
```
def say
    greeting = "Hello"
end

say # expecting it to set a variable called greeting

# greeting will still throw an undefined method or local variable error
puts greeting
```

The reason is because in ruby when you define a method, any variables defined inside are scoped to that method. Also any variables defined outside of the method can't be brought into the method without passing it through an argument. We call this methods scopes, so the variables that's defined `inside` the method would be inside the `methods scope`, as to where a variable defined outside of a `method` would be `outside` of that `method's scope`.
