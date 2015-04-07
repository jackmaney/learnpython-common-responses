# /r/learnpython common responses

## Goal

This repository intends to be a collection of good responses that can be used in reply to posts in /r/learnpython. The original idea, suggested by /u/elbiot, is that someone might write a Reddit bot that would post one of these responses when summoned.

## How to contribute

Either open an **issue** or send a **pull request**. If you haven't used Git and Github much, opening an issue will be much easier for you.

## The responses

For now, the responses are inlined here. If this file starts to get too long, I will split the responses into separate files.

### `formatting`: Formatting code for Reddit

To achieve properly-formatted code in a Reddit post or comment:

-	Prepend four spaces to each line of code.
-	Ensure blank lines separate the code from surrounding text.

For example, typing this

```
Use a list comprehension:

    squares = [x**2 for x in range(10)]
```

will produce a post that looks like this

> Use a list comprehension:
>
> ```
> squares =  [x**2 for x in range(10)]
> ```

### `gists`: Third party sites to host longer code blocks

If you have a long snippet of code that you don't already have in a code hosting site (eg [GitHub](https://github.com) or [Bitbucket](https://bitbucket.org/)) and that looks too unwieldy for an inline code block, consider creating a [gist](https://gist.github.com/) (requires a (free) GitHub account) or using [Pastebin](http://pastebin.com/).

### `mutable-default-value`: Avoid using mutable objects as default values

Avoid this:

```
class Box:
    def __init__(self, items=[]):
        self.items = items
```

Do this instead:

```
class Box:
    def __init__(self, items=None):
        if items is None:
            items = []
        self.items = items
```

Explanation: Default values are evaluated only once, when the function is defined, and stored with the function; calls to the function use those stored values. If you use `[]` as the default value, `[]` will be evaluated, producing an empty list, and that empty list will be stored. Every call to the function will use that same stored list object, so any modifications you make to it (such as appending items) will be seen by future function calls. To avoid this, you should use a default value of `None` and then construct the default value inside of the function.
