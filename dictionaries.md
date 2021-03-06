# Dictionaries
---

## Questions:
- How can I organize data to store values associated with labels?
- How do I work with such data structures?

## Learning Objectives:
- Be able to store data in dictionaries
- Be able to retrieve specific items from dictionaries
---

## Dictionaries are mappings

- Python provides a valuable data type called the **dictionary** (often abbreviated as "dict")
- Dictionaries are collections, like lists or strings
- However, dictionaries are *mappings*. Like a traditional dictionary that contains a word, followed by a definition, dictionaries are pairings of **keys** and **values**, contained in curly braces. For example:

~~~python
my_info = {'First Name':'Annikki', 'Last Name':'Bogdana', 'Age':15, 'Height':1.66}
~~~



```python
my_info = {'First Name':'Annikki', 'Last Name':'Bogdana', 'Age':15, 'Height':1.66}
```

Note that, like lists, dictionaries can contain a mixture of data types. Dictionary keys must be an immutable type, such as a string or number (int or float). Dictionary values can be any type. 

The values in a dictionary are accessed using their keys inside square brackets:

~~~python
my_info['First Name']
~~~


```python

```

Dictionaries provide a convenient way for labelling data. For example, in the previous lesson on lists, we used an example of a list of life expectancies for a country (Canada) for different years:

~~~python
life_expcy = [48.1, 56.6, 64.0, 71.0, 75.2, 79.2]
~~~

One limitation of using list like this, is that we don't know what years the values are associated with. For example, in what year was 48.1 the average life expectancy?

Dictionaries solve this problem, because we can use the keys to label the data. For example:

~~~python
life_expcy = {1900:48.1, 1920:56.6, 1940:64.0, 1960:71.0, 1980:75.2, 2000:79.2}
~~~


```python

```

## Dictionaries are mutable 

- We previously discussed the difference between *immutable* types like strings — whose contents cannot be changed — and *mutable* types like lists — which can be changed. Dictionaries are mutable.
- For example, we can add a new key:value pair by using the dict name plus square backets to specify a new key, followed by `=` to assign the value to this key:

~~~python
life_expcy[2020] = 83.2
print(life_expcy)
~~~


```python

```

- We can also change the value for an existing key in the same way. In the example above we assigned the wrong value to 2020; it should be 82.3 not 83.2. So we can fix it like this:

~~~python
life_expcy[2020] = 82.3
print(life_expcy)
~~~


```python

```

## Dictionary keys cannot be renamed
- Although dictionaries are mutable, we can't rename dictionary keys. However, we can delete existing entries and create new ones if we need to. 
- For example, below we add a life expectancy value for the year 2040, but we mistakenly make the key a string instead of an int like the other, existing keys:

~~~python
life_expcy['2040'] = 85.1
print(life_expcy)
~~~


```python

```

We can add another entry using the correct (int) key, but this doesn't delete the old entry:

~~~python
life_expcy[2040] = 85.1
print(life_expcy)
~~~

In the above example, rather than manually entering the new value manually, we can copy it from the value corresponding to the original (incorrect) key:

~~~python
life_expcy[2040] = life_expcy['2040']
print(life_expcy)
~~~


```python

```

We can remove a dictionary entry with the `del` statement. We learned about `del` in the lists lesson, including the fact that it is a Python *statement*, so it is followed by a space rather than parentheses:

~~~python
del life_expcy['2040']
print(life_expcy)
~~~


```python

```

## Dictionaries are *unordered*
- Another feature of both strings and lists is that they are *ordered* — the items exist in a string or list in a specific order. This is why we can use integers to index string or list items based on their position
- Dictionaries, in contrast, are *unordered*. You access values by their keys, but not using numerical indexing. For example, this will fail:

~~~python
life_expcy[0]
~~~


```python

```

If you run the code above, you will get a `KeyError`, because Python interprets what's in the square brackets as a dictionary key, not a sequential index. This makes sense, since dictionary keys can be integers.


```python

```

## Dictionaries have properties

Like other Python collections, dictionaries have a length property, which is the number of key:value pairs:

~~~python
len(life_expcy)
~~~


```python

```

## Viewing all the keys or values in a dictionary

You can view the entire set of keys in a dictionary like this:

~~~python
print(life_expcy.keys())
~~~


```python

```

Likewise, you can view all of the values using `.values()`:

~~~python
print(life_expcy.values())
~~~


```python

```

What Python type are the results of the `.keys()` and `.values()` methods?

## Dictionary values can be any type

While dictionary keys must be an immutable type, such as strings or numbers, values can be any type — including lists, or other dictionaries.

For example, here we create a dictionary in which each key is a country name, and the value is a list of life expectancies for different years:

~~~python
intl_life_expcy = {'Canada':[48.1, 56.6, 64.0, 71.0, 75.2, 79.2],
                   'Denmark':[51.3, 57.5, 66.1, 72.0, 74.2, 77.0],
                   'Egypt':[32.7, 32.6, 33.8, 46.9, 58.0, 68.7]
                  }
print(intl_life_expcy['Egypt'])
~~~


```python

```

Using lists in the above example has the same limitation talked about at the start of this lesson: we don't know what years correspond to the values in each list. Using a dictionary of dictionaries solves this problem: 

~~~python
intl_life_expcy = {'Canada':{1900:48.1, 1920:56.6, 1940:64.0, 1960:71.0, 1980:75.2, 2000:79.2},
                   'Denmark':{1900:51.3, 1920:57.5, 1940:66.1, 1960:72.0, 1980:74.2, 2000:77.0},
                   'Egypt':{1900:32.7, 1920:32.6, 1940:33.8, 1960:46.9, 1980:58.0, 2000:68.7}
                  }
print(intl_life_expcy['Egypt'])
~~~

We can now obtain values for specific years, within specific countries, using a sequence of keys, working from the outside in:

~~~python
print(intl_life_expcy['Denmark'][1940])
~~~


```python

```

## Summary of Key Points
- dictionaries are a special type of collection called *mappings*
- each dictionary entry is specified as a key:value pair
- key:value pairs are assigned to variable names within curly braces: `{}`
- keys must be immutable types, such as strings or numbers. 
    - however, dictionary values can be any Python type, including lists or other dictionaries
- dictionaries are mutable, in that one can add or delete entries, or change the value of an entry
    - however, dictionary keys cannot be renamed. Instead, you must delete the old key:value pair and create a new one
- dictionaries are unordered, so you cannot access an entry based on its serial (sequential) position the way you can entries in a list
    - instead, you access values based on their keys
- the length of a dictionary is the number of key:value pairs it contains
- you can see a list of all dictionary keys or values using the `.keys()` and `.values()` methods, respectively

---
Licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/) 2021 by [SURGE](https://github.com/surge-dalhousie)
