# Ruby

`puts` prints to console and adds new line

`print` prints but does not add a new line

single lines comments begin with `#`

multi-line comments are as such 
```ruby
=begin
prints 2 to console with new line
chocoloate is cool
=end
puts 2 
```

`gets` gets input from the user and automatically adds a new line after. 
```ruby
# will get input but not add new line
gets.chomp
```

`#{variable}` will select variable and interporalate in strings

Using `!` at the end of a method will assign the value of as a result of the method execution to that same variable
```ruby
# assigns name to JJ
name = jj
name.upcase!
```

#### conditionals
Uses `if`, `elsif`, and `else`

Uses `&&` and `||`

no needs for ":" or ";"

At the end of a conditional block, must indicate `end` on new line

Can use `unless` to check for false things. "Unless x is true, do b"
```ruby
# prints "I'm eating"
not_eating = false
print "I'm eating" unless not_eating
```

#### Loops and Iterators 

`until` is like a backwards while loop

For loop:
`...` is exclusive of last num
`..` is inclusive of last num

```ruby
# prints 1 to 9
for nums in 1...10
  puts num
end
```

`loop {do a thing}` is the same as `loop do ............ end`

use `break` condition to end a loop

use `next` to skip parts or conditions of a loop

Can use `.each`
```ruby
# item is a parameter
object.each { |item| 
  # Do something 
}

object.each do |item| 
  # Do something 
end
```

```ruby
# print string 10 times
10.times { puts "hi" }
```

objects represented with hashes with properties `key => value`
Can create new hash like this
```ruby
# creates an empty hash
my_hash = Hash.new
```



