---
layout: post
title:  "Open-source Contributions"
date:   2020-04-24 22:21:49 +1000
categories: ML
permalink: /:title.html
---

Since I am somtimes fascinated with open-source contributions (in contrast to my research, I personally feel more enengy for this work), I think it will be helpful for me (or others) to summarize some challenges for the workflow to contribute (make a pull request). Here I take the example of one libray I contribute on --- [`AllenNLP`](https://github.com/allenai/allennlp).

# Basic: Python packages
From my experience, delving into Python open source means that we transfer from using Python as a scripting language to Python modular programming. Therefore, the terms like **module**, **package** are everywhere whenever I come across problems related to the accessibility of my code and understand the mechanism of Python running environment. I look over relevant parts of [official documentation](https://packaging.python.org/) every time when these problems happen to me. I always think it is a good idea to read relevant contents in a goal-oriented way, summarize with practice and finally we may have the big picture of Python mechanism (since I am not a Python core developer).

* Python Module: e.g., `allennlp/data/vocabulary.py` or a package with `__init__.py` file. 
    > [Module](https://docs.python.org/3/tutorial/modules.html): The basic unit of code reusability in Python.
    >
    > `__init__.py` is required to import the directory as a package, and should be empty.

* Module vs Package:
    > It’s important to keep in mind all packages are modules, but not all modules are packages. Or put another way, packages are just a special kind of module. Specifically, any module that contains a __path__ attribute is considered a package.
    --- from [Python Docs: Packages](https://docs.python.org/3/reference/import.html#packages)

* Distribution Package v.s. Import Package: 

    > [Distribution Package](https://packaging.python.org/glossary/#term-Distribution-Package): A versioned archive file that contains Python packages, modules, and other resource files that are used to distribute a Release.
    >
    > [Import Package](https://packaging.python.org/glossary/#term-Import-Package): A Python module which can contain other modules or recursively, other packages.




# How to test the code for Pull Request (PR) ?

`pytest` is the tool to perform unit test on Python modules. Before we perform tests, we need to make `allennlp` a module with `__init__.py` file in the directory. So the test file can access the Python file it tests on.

1. Focus on two directories: (1) `allennlp` directory is for the application, (2) and `tests` diectory for unit test.

2. Find corresponding test file in `tests` directory for the module you want to test in `allennlp`. For example, I need to use `tests/interpret/hotflip_test.py` for testing my PR for `allennlp/interpret/attackers/hotflip.py`.

```python
from pytest import raises
from allennlp.interpret.attackers import Hotflip
```

