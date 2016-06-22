# What Is Big O

## Objectives

1. Understand what Big O notation is
2. Calculate Big O of a method

## What is Big O notation?

Big O notation is a CS term that is used to describe how much space or how much time a method (or algorithm) takes in a worst case scenario. You'll usually see the complexity of an algorithm described in some of the following ways: O(1), O(n), O(n log(n)).

Using this notation, we can compare the complexity of different algorithms. The [Big O complexity chart](http://bigocheatsheet.com/#chart) shows the relative complexity of all of the Big O classifications.

## How to calculate the time complexity of a problem

In the most basic sense, Big O calculates how many steps a computer takes to run a method.

For example, let's look at the following two methods:

Method 1

```ruby
def square(number)
  number * number
end
```

Method 2

```ruby
def square(number)
  answer = 0
  number.times do
    answer = answer + number
  end
  answer
end
```

Both of these methods will return the same number if they are given the same input. Just from looking at these two, you can probably tell that Method 1 is less complex than Method 2, but Big O is a formal way of calculating this.

Method 1 only takes 1 step and no matter how large our number is, it'll always take only one step. We call this O(1), or constant time as the time required is relatively constant regardless of our input.

Method 2 will take more steps for the computer to solve. We're setting extra variable and iterating. It quickly becomes clear though that the number of steps the computer needs to take to solve this will be related to how large of an input we give to the method. If our number is 1000, then in addition to a few extra set up steps, the computer is going to be taking 1000 steps to solve this. We call this O(n) because there is a linear relation between the size of our input and the number of steps needed.

Take a look at [Rob Bell's blog](https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/) to get an idea of how to calculate Big O notation.

## Tips to quickly computing complexity

COUNT THE NESTED LOOPS!

Without going through in depth analysis, this will give us a quick estimate of complexity. Taking another look at the examples above, we see that Method 1 has no loops in it and it's O(1). Method 2 on the other hand loops through once and it depends on our input and this is O(n).

Now let's take a look at another example where we have a grid and we want to sum all the values stored in this grid:

Method 3

```ruby
grid = [[1,6,3],
        [0,3,1],
        [9,7,8]]
def sum_of_grid(grid)
  sum = 0
  grid.each do | row |
    row.each do | column |
      sum = sum + column
    end
  end
  sum
end
```

Now we have a nested loop and our complexity is O(n^2).

Another thing that you want to make sure you watch out for is secret iterators that are looping through your data. Some examples of these are `#include?` and `#any?`. Think about how these work, they're gonna have to look at all your data to be able to return a truthful answer.

Here's another example method using a secret iterator:

Method 4

```ruby
grid = [[1,6,3],
        [0,3,1],
        [9,7,8]]
def includes_an_eight?(grid)
  answer=false
  grid.each do | row |
    answer = true if row.include?(8)
  end
  answer
end
```

Method 4 would still have a Big O complexity of O(n^2). We see that we have to iterate through our rows in our grid and then we call `#includes?` which iterates through each item for every row!

## Why is it important?

Big O notation can be important because it can help us compare different ways to write the same method. A great place to see this in action is over at [The Big O Cheat Sheet](http://bigocheatsheet.com/).

This web page displays the time and space complexity of all sorts of different algorithms and is definitely worth a look.

## Moving Forward

Really take a look at [The Big O Cheat Sheet](http://bigocheatsheet.com/). Make sure that you know that the fastest sorting algorithms are O(n log(n)).

As you work on the rest of the labs in this section (and in interviews) it would be good to have a general idea of the time complexity of your methods. Try and count your nested loops and avoid them where you can.

## Resources

* [Big-O notation explained by a self-taught programmer](https://justin.abrah.ms/computer-science/big-o-notation-explained.html)

<a href='https://learn.co/lessons/what-is-big-o' data-visibility='hidden'>View this lesson on Learn.co</a>
