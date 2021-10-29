---
aliases: [Python Import Explained, Import Patterns, Python Import Patterns]
tags: [python, code, example, how-to]
status: ongoing
edited: 2021-10-28
---

# Python Import Patterns
(This is from this [article](https://towardsdatascience.com/whats-init-for-me-d70a312da583))

How you shape a package changes how you use the package.
In other words, how you decide to use the package will determine how to shape `__init__.py` for the package.

There are three ways to shape a package:
- The General Store
- The Convenience Store
- The Online Store

Before we get started, let's make an example package, called `apackage`.
Structure like so:
```
/src
	/apackage
		__init__.py
		foo.py
		bar.py
		baz.py
	main.py
```

codes:
```python
# foo.py
def foo_func():
    print('this is a foo function')

# bar.py
def bar_func():
    print('this is a bar function')

# baz.py
def baz_func():
    print('this is a baz function')
```

`main.py` is the user implementation of the package.

## The General Store
This approach allows a user to get access to everything right away on `import apackage`.

```python
# __init__.py
from .foo import *
from .bar import *
from .baz import *

# main.py
import apackage

apackage.foo_func()
apackage.bar_func()
apackage.baz_func()
```

### Advantages
1. Users need not call a module (e.g. `from apackage import foo`) to access a function inside the module. You can, but you don't have to.
2. Tab completion gives you everything on `apackage.<TAB>`.
3. When modules are added, there is no need to update import statements on the user implementation side.

### Disadvantages
1. Requires that all functions/classes must be uniquely named.
2. If the package is large, it can add a lot to the namespace and (depending on a lot of factors) can sow things down.
3. Requires a bit more effort to hide some elements (e.g. `_purge()`) from the user.

### Use this structure when
1. When it is hard to predict the workflow of a typical user.
2. When the user might frequently bounce between modules.
3. When using modules will not improve readability.
4. When the package has a few modules. Otherwise, it would be difficult for the user to navigate the documentation to find the functionality they want.
5. When objects might be added/removed frequently.

### Well-known examples
- `pandas`
- `numpy`
- `seaborn`

## The Convenience Store
This approach allows a user to get access to a small number of things.
It's the small scale version of The General Store approach.
It has a bit more order, and less clutter.

```python
# __init__.py
from .foo import foo_func()
from .bar import bar_func()

# main.py
import apackage

apackage.foo_func()
apackage.bar_func()
apackage.baz_func() # this will error
```

### Advantages
1. It shares all the advantages of The General Store approach.
2. Availability of objects are controlled.

### Disadvantages
1. `__init__.py` can get cluttered.
2. If a function is added, the developer has to decide whether to expose it, then have to make sure it gets added on `__init__.py`.

### Use this structure when
1. When the user only needs to use a small number of things from the package.
2. When it's obvious which objects the user needs.
3. When you don't expect to add/remove objects frequently.

### Well-known example
- `geopandas`

## The Online Store
This allows user to browse through categories to find the object they want.
In other words, modules come into play.

```python
# __init__.py
import apackage.foo
import apackage.bar
import apackage.baz
```

There are three ways a user can use `apackage` with this approach.

```python
import apackage
apackage.foo.foo_func()
apackage.bar.bar_func()
apackage.bar.baz_func()
```
or
```python
from apackage import foo, bar, baz
foo.foo_func()
bar.bar_func()
baz.baz_func()
```
or
```python
import apackage.foo as ex_foo
import apackage.bar as ex_bar
import apackage.baz as ex_baz
ex_foo.foo_func()
ex_bar.bar_func()
ex_baz.baz_func()
```

### Advantages
1. Simplifies `__init__.py`. Only needs to be updated when a new module is needed.
2. It is flexible. User can import everything, or import a few modules.
3. Aliasing a long module is possible.
4. Can have multiple objects with the same name.

### Disadvantages
1. It may be complicated to find which package a module belongs to. For example, `foo.foo_func()` does not indicate which package `foo` comes from.
2. User implementation can become needlessly long. For example, `apackage.foo.foo_func()`.

### Use this structure when
1. When there are complex series of modules.
2. When importing the whole package imports a lot of objects and might be slow.
3. When you can clearly define workflows for different types of users.

### Well-known examples
- `matplotlib` (e.g. `import matplotlib.pyplot as plt`)
- `scikit-learn`
- `bokeh`
- `scipy` (e.g. `import scipy.stats.kde`)

