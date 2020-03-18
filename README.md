## The Enumerable Family Tree

## Learning Goals

* Use `map` to transform an `Array`
* Use `reduce` to reduce an `Array` to a value
* Use Ruby documentation to learn more about other variations on `map` and
  `reduce`
* Use `select` and `reject` to filter an `Array`
* Provide a list of Enumerables to memorize

## Introduction

Now that you have written some methods using `each`, we're going to look at some
of the many Enumerables available to us.

As programmers, we wonder about the world, come up with questions and then ask a
computer to help us manipulate data to find answers. Many of those questions can
be resolved by either:

- "Polling" every member in a collection and collecting the results into a new
  collection through a process called "mapping" (or)
- "Polling" every member in a collection and joining those poll's results
  together into a single value through a process called "reducing"

Ruby has two Enumerables that do these tasks - `map` and `reduce`. Let's take a
look at both and see how the work.


## Use `map` to Transform an `Array`

The `map` method enumerates over a collection, performs work using each element,
and returns a **new collection**. For example, if we had an array of numbers, we
could use `map` to perform an operation on each number and collect the results.

```ruby
[10, 20, 30, 40].map do |num|
   num * 2
end
 # => [20, 40, 60, 80]
```

The above code returns a new array where each element is a double of the
original. Here is another example, written with curly braces:

```ruby
[5, 10, 15, 20, 25].map { |num| num.even? } # => [false, true, false, true, false]
```

Above, we're collecting the boolean result of checking every element to see if
it is an even number. The value returned from inside the block (`num.even?`) is
collected each time and stored in the array that is returned at the end.

This chart shows a few examples and comparisons regarding `map`:

![Ruby Enumerables](https://curriculum-content.s3.amazonaws.com/ruby-enumerables/enumerables-family-tree/Image_78_RubyMapTree.png)

## Use `reduce` to Reduce an `Array` to a Value

The `reduce` method enumerates over a collection, aggregating the results into a
single value. `reduce` can be used to add all the values in an array together to
get a total:

```ruby
[10, 20, 30, 40].reduce(0){ |total, num| total + num } #=> 100
```

Notice that `reduce` has a block _and_ an argument. In the examples above, the
argument is `0`. This is the **initial value**. The block contains two
parameters, `total` and `num`. For the first element in the array being reduced,
`total` is initially set to `0`, and `num` is equal to `10`. The block returns
the result of adding these two numbers. The returned value becomes `total` the
next time the block is called. So for the second element in the array, `total`
is now equal to `10` (`0` + `10`), and `num` is `20`, resulting in `30`. For the
third element, `total` is `30` and num is `30`. Finally, for the last element,
`total` is `60` and `num` is `40`. The result of this final addition is returned
and the array has been reduced down to `100`.

If we pass a different value into `reduce`, we'll start off with a different
initial value:

```ruby
[10, 20, 30, 40].reduce(100){ |total, num| total + num } #=> 200
```

More complex implementations of `reduce` can actually be used to build hashes
and nested data structures.

```ruby
["bird", "plane", "bird", "superman"].reduce({}) do |accumulator, value|
   if accumulator[value]
      accumulator[value] += 1
   else
      accumulator[value] = 1
   end
   accumulator
end
 # => {"bird"=>2, "plane"=>1, "superman"=>1}
```

The above code takes an array and reduces it, returning a hash that contains a
count of each element from the original array. Notice that in this example, we
_must_ return `accumulator` at the end of the block after it has been modified.
The returned value becomes the _next_ block's `accumulator`.

## Use Ruby Documentation to Learn More About Other Variations on `map` and `reduce`

Now that we understand the character of Enumerable methods and the code
behind using blocks, you are ready to unleash the full power of this module!
Instead of merely repeating the documentation, we're going to help you apply
your understanding to the `select` and `reject` methods, and then we're going
to give you a list of document resources you should look up and master.

## Select / Reject

```ruby
[10, 20, 30, 40].select{ |num| num > 25 } #=> [30, 40]
```

`select` maps over a collection, but only collects the elements that return a
truthy value in the block. Ruby also lets you do this work by calling the
method `filter`, which operates the same way.

`reject` does the opposite. It maps over a collection, but only collects the
elements that _do not_ return a truthy value in the block.

```rb
[10, 20, 30, 40].reject{ |num| num > 25 } #=> [10, 20]
```

## Provide a List of Enumerables to Memorize

These are the Enumerables you should ***memorize*** and practice heavily.
They're going to be your friends every day in Ruby-land. There are other
Enumerables that you might not memorize, but it's pretty common for a developer
to realize that they're working in the "Character of Enumerable Methods" and
think, "Hmm, maybe there's an Enumerable for that...." When that moment hits,
the developer comes _back_ to the documentation and look for that "just-right"
Enumerable.

* [`all?`][all?]: Everything "tested" by the block returns truthy
* [`any?`][any?]: Did anything "tested" by the block returns truthy
* [`collect`][collect]: A synonym for `map`
* [`count`][count]: Which elements satisfy the block _or_, without block, how many elements are there?
* [`detect`][detect]: Which element satisfies the block _first_. Does the same thing as `find`.
* [`find_all`][find_all]: Which elements satisfy the block?
* [`find_index`][find_index]: What is the index of the first element to satisfy the block?
* [`max`][max]: What's the highest value?
* [`max_by`][max_by]: What's the highest value based on some property of the element?
* [`min`][min]: What's the lowest value?
* [`sort`][sort]: Put the values in order

## Conclusion

Your programming power just increased by at least 10-fold. With these methods,
and others provided in the documentation, you can tear through datasets
efficiently and flexibly. Enjoy the power!

These Enumerables will help you solve most questions about collections. Some of
the Enumerables in the documentation might look a bit scary or make you wonder
"When the heck would I ever use that?" But over time, as you become more
practiced, you'll be amazed to see these methods rush to your aid!

[all?]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-all-3F
[any?]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-any-3F
[collect]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-collect
[count]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-count
[detect]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-detect
[find_all]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-find_all
[find_index]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-find_index
[max]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-max
[max_by]:https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-max_by
[min]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-min
[sort]: https://ruby-doc.org/core-2.6.3/Enumerable.html#method-i-sort


