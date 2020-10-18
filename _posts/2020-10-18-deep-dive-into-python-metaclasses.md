---
layout: post
title: Deep dive into Python Metaclasses
date: 2020-10-18T18:57:45.478Z
updated_date: 2020-10-18T18:57:45.498Z
published: true
image: https://images.unsplash.com/photo-1515879218367-8466d910aaa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1650&q=80
tags:
  - python
  - programming
categories:
  - python
  - programming
  - productivity
author_name: Prashant Sharma
author_username: sharma_pacific
show_ads: false
show_telegram_signup: false
canonical_url: https://sharmapacific.in/metaclasses-in-python/
---
{% include lazyload.html image_src="https://images.unsplash.com/photo-1515879218367-8466d910aaa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1650&q=80" image_alt="Deep dive into Python Metaclasses" image_title="Deep dive into Python Metaclasses" %}

In most programming languages, classes are just pieces of code that define the rules for an object, but in Python, as you must hear that everything is an object: it turns out that this is true of classes themselves. Classes are actually first-class objects, they can be created at runtime, passed as parameters, returned from functions, and assigned to variables.

Let's look at the below example -

```python
class Tutorial:
    pass

print(Tutorial())

# Output - 
# <__main__.Tutorial object at 0x7fd92c1500f0>
```

As we can see the instance of the `Tutorial` class tells us that this is an object of the main Tutorial object at some location.

Now just print the class itself -

```python
print(Tutorial)

# Output - 
# <class '__main__.Tutorial'>
```

The reason we're able to do this because the `Tutorial` class is an object, just like any other object. When you use the `class` keyword, Python creates this object automatically. It's an instance of a metaclass - `type`.

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/bgrlcqvkq3y9bd9jtkt3.jpg)

> A metaclass is the class of a class; it defines how a class behaves.

Now for making it easier, let go into depth, Maybe you have come across the `type` keyword in Python? Which used to finding the Type of an Object -

```python
print(type(1))

# Output - 
# <class 'int'>

print(type('Hey'))

# Output - 
# <class 'str'>
```

As expected `1` is the type of `int` class, `Hey` is the type of `str` class, let's find out the Type of our Class - 

```python
print(type(Tutorial))

# Output - 
# <class 'type'>
``` 

This time, we get a printout that `Tutorial` is of type of class `type`. But what about the `type` itself? What is the type's `type`?

```python
print(type(type))

# Output - 
# <class 'type'>
```

The type of `type` is class `type`, you maybe find this weird. Thus we find that `type` is also its own metaclass!

## Understanding How Metaclasses Work

`type` is a built-in metaclass in python. it is used to construct classes just like a class is used to construct the objects. So Whenever we create any class then the default metaclass(`type`) gets called and giving us an option to use it as an object.
That means every class in python is also an object of `type`, Therefore We can use `type` directly to make a class, without any class syntax. The type() function can be used to directly define classes by using the following three arguments -

```python
type(<name>, <bases>, <dct>)
```

* **name** - This is the internal representation of the class. This is the name of the class.

* **bases** - This specifies anything that we inherit from a superclass or a parent class. This is a tuple of the parent class.

* **dct** - This specifies a namespace dictionary containing definitions of class's methods and variables.

To make it more clear -

```python
Test = type('Test', (), {})
```

so the above line of code is completely equivalent to this below code -

```python
class Test:
    pass
```

There's absolutely nothing different about them.

Hence, if we want to modify the behavior of classes, we will need to write our own custom `metaclass`.

To create our own custom metaclass, we first have to inherit the default metaclass `type`, and implement the metaclass's `__new__` method and/or `__init__` method.

* `__new__`: This dunder method is usually overridden type's `__new__`, to modify some properties of the class to be created, 
before calling the original `__new__` which creates the class.

* `__init__`: This method is called when you want to control the initialization after the instance/object has been created.


```python
class MyMeta(type):
    def __new__(self, name, bases, attr):
        print(attr)
        return type(name, bases, attr)
```

So here I have defined a simple metaclass `MyMeta`, and we're just going to print out the attributes so we can see how they look like. after that, I have defined another class `Sample` and it's having the metaclass `MyMeta`, with `name` and `age` variable -

```python
class Sample(metaclass=MyMeta):
    name = 'bob'
    age = 24
```

Now without creating an instance this stills runs as you can see the output below - 

```python
{'__module__': '__main__', '__qualname__': 'Sample', 'name': 'bob', 'age': 24}
```

So how this class `Sample` has been created -

Interpreter sees `metaclass=MyMeta` defined in `Sample`, So now the interpreter has information that default metaclass `type` must not be used to create `Sample` class, Instead, `MyMeta` must be used to create `Sample` class.

So, the interpreter makes a call to `MyMeta` to create class `Sample`, When `MyMeta` is got called, `__new__` of `MyMeta` is invoked and it prints out the attributes and using `type` its construct the instance of `MyMeta` which is `Sample` and returns to us the object.

This metaclass only overrides object creation. All other aspects of class and object behavior are still handled by type.

Now We've covered enough theory to understand what metaclasses are and how to write custom metaclasses. Now let's look a simple real case scenario -

Let's suppose we have a requirement that all attributes of your class should be in upper case, There are multiple ways to achieve this functionality, but here we are going to achieve this using `metaclass` at the module level, So in namespace dictionary(attributes) if a key doesn't start with a double underscore we need to change it to be uppercase -

```python
class MyMeta(type):
    def __new__(self, name, bases, atts):
        
        print(f'current_attributes - {atts}\n')
        new_atts = {}
        
        for key, val in atts.items():
            if key.startswith('__'):
                new_atts[key] = val
            else:
                new_atts[key.upper()] = val

        print(f'modified_attributes - {new_atts}')        
        return type(name, bases, new_atts)


class Sample(metaclass=MyMeta):
    x = 'bob'
    y = 24
    
    def say_hi(self):
        print('hii')
```

Output - 

```python
current_attributes - {'__module__': '__main__', '__qualname__': 'Sample', 'x': 'bob', 'y': 24, 'say_hi': <function Sample.say_hi at 0x7fd92c10d048>}

modified_attributes - {'__module__': '__main__', '__qualname__': 'Sample', 'X': 'bob', 'Y': 24, 'SAY_HI': <function Sample.say_hi at 0x7fd92c10d048>}
```

As you can see above we have printed the current attributes and created a dictionary that we used to represent our modified attributes.

Here we are just checking if the key starts with a double underscore then just adds the proper value otherwise we are adding the uppercase attribute with that corresponding value.

Now to make sure that this is working let's try, I have created an instance of `Sample`, and just print one of the old attributes.

```python
s = Sample()
s.x
```

Output - 

```python
AttributeError Traceback (most recent call last)
<ipython-input-18-87b2922593a9> in <module>
      1 s = Sample()
----> 2 s.x

AttributeError: 'Sample' object has no attribute 'x'
```

As expected we have got an error `AttributeError`, which is totally fine because we have just modified the construction of the object, let's try to access by modified attributes -

```python
print(s.X)

s.SAY_HI()
```
Output - 
```python
bob
hii
```

This is why they call it magic because with this kind of hook into the creation of classes you can really enforce quite a bit of constraint on how classes are created

So for example, if you want every single class in a specific module to never be allowed to use a certain attribute or to follow a specific pattern you could set metaclasses for those specific modules. 

## Conclusion

The purpose of metaclasses isn't to replace the class/object distinction with metaclass/class - it's to change the behavior of class definitions (and thus their instances) in some way.
A reasonable pattern of metaclass use is doing something once when a class is defined rather than repeatedly whenever the same class is instantiated. When multiple classes share the same special behavior, repeating `metaclass=X` is obviously better than repeating the specific purpose code.