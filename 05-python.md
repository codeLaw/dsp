# Learn Python

Read Allen Downey's [Think Python](http://www.greenteapress.com/thinkpython/) for getting up to speed with Python 2.7 and computer science topics. It's completely available online, or you can buy a physical copy if you would like.

[![Think Python](img/think_python.png)](http://www.greenteapress.com/thinkpython/)

For quick and easy interactive practice with Python, many people enjoy [Codecademy's Python track](http://www.codecademy.com/en/tracks/python). There's also [Learn Python The Hard Way](http://learnpythonthehardway.org/book/) and [The Python Tutorial](https://docs.python.org/2/tutorial/).

Complete the following exercises to check your ability with Python.

These exercises are implemented with doctests, which are runnable tests inside docstrings. Fill in the function definitions. Correct solutions will make it possible to run (for example) `python -m doctest strings.py` with no messages about failures.

 * [Strings](python/strings.py)
 * [Lists](python/lists.py)


---

How are Python lists and tuples similar and different? Which will work as keys in dictionaries? Why?

>Lists and tuples are similar in that both are a sequence of elements of any kind (e.g., integer, float, string) that can be indexed by integers.  A key difference between the two is that lists are mutable (i.e., changeable) while tuples are not.  Lists are enclosed by square brackets while tuples are enclosed by parenthesis.  Dictionary keys are immutable and therefore tuples will work as keys in dictionaries.


---


---

How are Python lists and sets similar and different? Give examples of using both. How does performance compare between lists and sets for finding an element. Why?

>Similar to lists, sets are a collection of elements, however, unlike lists, sets contain only mutable non-duplicate items.  Sets are an unordered collection of elements and therefore do not support indexing or slicing.  

>An example of a list:

>a=[‘a’,’b’,’b’,’c’]
>>Out[1]: ['a', 'b', 'b', 'c']

>An example of a set:

>set(['a','b','b','c'])
>>Out[2]: {'a', 'b', 'c'}

>Because sets use hashtables while lists evaluate each individual item, it is generally faster to search a set than a list, especially for large sets/lists.


---


---

Describe Python's `lambda`. What is it, and what is it used for? Give at least one example, including an example of using a `lambda` in the `key` argument to `sorted`.

>The lambda operator or lambda function is a way to create small anonymous “throw-away” functions (i.e., functions without a name that are used only once). 

>An example:

>tuples =  [(1, 7), (1, 3), (3, 4, 5), (2, 2)]

>tuples = sorted(tuples, key=lambda item: item[len(item)-1])
>>Out[3]: [(2, 2), (1, 3), (3, 4, 5), (1, 7)]


---


---

Explain list comprehensions. Give examples and show equivalents with `map` and `filter`. How do their capabilities compare? Also demonstrate set comprehensions and dictionary comprehensions.

>The lambda operator or lambda function is a way to create small anonymous “throw-away” functions (i.e., functions without a name that are used only once). 

>An example:

>tuples =  [(1, 7), (1, 3), (3, 4, 5), (2, 2)]

>tuples = sorted(tuples, key=lambda item: item[len(item)-1])
>>Out[3]: [(2, 2), (1, 3), (3, 4, 5), (1, 7)]




Explain list comprehensions. Give examples and show equivalents with map and filter. How do their capabilities compare? Also demonstrate set comprehensions and dictionary comprehensions.

>List comprehensions are used to create a series (any combination of list, set, tuple).  As its name suggests, filter( ) filters the elements of a list (i.e., removes items which the function determines are False) and returns a list of “True” items.  In contrast, map( ) applies a function to each element in a list and returns that list of “applied” elements. 

>List
>numbers = [x*10 for x in range(5)]
>numbers
>>Out[4]: [0, 10, 20, 30, 40]

>Map
>map(lambda x: x*10, range(5))
>>Out[5]: [0, 10, 20, 30, 40]

>Or, without lambda:

>def timesten(x):
>    x = x*10
>    return x

>map(timesten, range(5))
>>Out[6]: [0, 10, 20, 30, 40]

>Filter
>numbers = [i for i in range(5) if i % 2 == 0]
>numbers
>>Out[7]: [0, 2, 4]

>Set Comprehension
>s = { x for x in range(5) }
>>Out[8]: {0, 1, 2, 3, 4}

>Dictionary Comprehension
>D = {k: 0 for k in ['a','b','c']}
>D
>>Out[9]: {'a': 0, 'c': 0, 'b': 0}

---


Write a Markov text generator, [markov.py](python/markov.py). Your program should be called from the command line with two arguments: the name of a file containing text to read, and the number of words to generate. For example, if `chains.txt` contains the short story by Frigyes Karinthy, we could run:

```bash
./markov.py chains.txt 40
```

A possible output would be:

> show himself once more than the universe and what I often catch myself playing our well-connected game went on. Our friend was absolutely correct: nobody from the group needed this way. We never been as the Earth has the network of eternity.

There are design choices to make; feel free to experiment and shape the program as you see fit. Jeff Atwood's [Markov and You](http://blog.codinghorror.com/markov-and-you/) is a fun place to get started learning about what you're trying to make.
