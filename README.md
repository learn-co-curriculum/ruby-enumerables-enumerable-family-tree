## The Enumerable Family Tree

## Learning Goals

* Use `map` to transform an `Array`. 
* Use `reduce` to reduce an `Array` to a value.
* Use Ruby documentation to learn more about other variations on `map` and
  `reduce`.
* Use `select` and `reject` to filter an `Array`.
* Provide a list of Enumerables to memorize.

## Introduction

Now that you have written `map` and `reduce`, here's the big reveal: Ruby
_already_ has these methods built into its `Array` data type!

![Ruby Enumerables](https://curriculum-content.s3.amazonaws.com/ruby-enumerables/enumerables-family-tree/Image_78_RubyMapTree.png)

## Use `map` to Transform an `Array`

```ruby
[10, 20, 30, 40].map{ |num| num * 2 } #=> [20, 40, 60, 80]
```

## Use `reduce` to Reduce an `Array` to a Value

```ruby
[10, 20, 30, 40].reduce(0){ |total, num| total + num } #=> 100
[10, 20, 30, 40].reduce(100){ |total, num| total + num } #=> 200
```

While it was work for us to learn to code these and deal with blocks, using
these features is just a few keystrokes!

## Use Ruby Documentation to Learn More About Other Variations on `map` and `reduce`

Now that we understand the "Character of Enumerable Methods" and the code
behind using blocks, you are ready to unleash the full power of this module!
Instead of merely repeating the documentation, we're going to help you apply
your understanding to the `select` and `reject` methods, and then we're going
to give you a list of document resources you should look up and master.

## Select / Reject

```ruby
[10, 20, 30, 40].select{ |num| num > 25 } #=> [30, 40]
[10, 20, 30, 40].reject{ |num| num > 25 } #=> [10, 20]
```

1. Map a collection
2. Only accumulate the elements that make a truthy expression in the block for
   `select`.
3. Only accumulate the elements that don't make a truthy expression in the
   block for `reject`.

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
* [`collect`][collect]: Does the same thing as `map`
* [`count`][count]: Which elements satisfy the block _or_, without block, how many elements are there?
* [`find`][detect]: Which element satisfies the block _first_. Does the same thing as `detect`.
* [`find_all`][find_all]: Which elements satisfy the block? Does the same thing as `select`.
* [`find_index`][find_index]: What is the index of the first element to satisfy the block?
* [`max`][max]: What's the highest value?
* [`max_by`][max_by]: What's the highest value based on some property of the element?
* [`min`][min]: What's the lowest value?
* [`sort`][sort]: Put the values in order

## Conclusion

Your programming power just increased by at least 10-fold. With these methods,
and others provided in the documentation, you can tear through datasets
efficiently and flexibly. Enjoy the power!


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


These Enumerables will help you solve most questions about collections. Some of
the Enumerables in the documentation might look a bit scary or make you wonder
"When the heck would I ever use that?" But over time, as you become more
practiced, you'll be amazed to see these methods rush to your aid!
