---
layout: post
title: Understanding Rust Ownership
tags: Rust TheRustProgrammingLanguageBook StudyNotes
---

This is a series of study notes I took while learning Rust.

## The Stack v.s. the Heap

First of all, let's clarify that the phrase “allocating memory” generally means asking the operating system to find an empty spot on the heap and make it available for use.

Accessing data in heap is generally slower than stack because:

1. we have to follow a pointer to get to the actual data.
2. Modern CPUs are faster at accessing contiguous memory pages, which is normally how stacks are implemented. On the contrary, the heap is just like a free-range farm.

Ownership exists to manage data on the heap.

## Ownership Rules

Here are the slightly modified version of the original 3 rules:

```
1. Each value in Rust has one and only one owner at any given time.
2. When the owner goes out of scope, the value will be automatically dropped (i.e. deallocated)
```

Let's go over some observations derived from the rules.

### Move v.s. Clone

**Move:** Transfer the ownership of a piece of data on the heap to another owner.
**Clone:** Allocate new memory section on the heap and and copy the data over. It will be owned by a new owner.

An example of move:

{% highlight rust linenos %}
let s1 = String::from("hello");
let s2 = s1; // s1 is invalidated after this line. It was "moved".
{% endhighlight %}

An example of copy:

{% highlight rust linenos %}
let s1 = String::from("hello");
let s2 = s1.clone(); // s1 is still valid after this line because it's not moved. Instead a new copy with a new owner is created
{% endhighlight %}

### Immutable Borrowing v.s. Mutable Borrowing

You can use the `&` operator to “borrow” a piece of heap data. The default behavior is that you can read but can not modify it. In order to borrow and mutate it, you have to use `&mut`. Beware that you can not create mutable borrowing multiple times in the same scope nor can you create both mutable and immutable borrowing in the same scope.

{% highlight rust linenos %}
// Can not create mutable borrowing:
let mut s = String::from("hello");

let r1 = &mut s;
let r2 = &mut s; // incorrect
{% endhighlight %}

{% highlight rust linenos %}
// Can not create both immutable and mutable borrowing:
let mut s = String::from("hello");

let r1 = &s;
let r3 = &mut s; // incorrect
{% endhighlight %}

## Reference

1. [The Rust Programming Language - Ch 04 “Understanding Ownership”](https://doc.rust-lang.org/book/second-edition/ch04-00-understanding-ownership.html)