---
aliases: [How to Parallelize with Verstack, Issue with Verstack Multicore]
tags: [python, code, example, how-to, verstack, issues, multicore, parallel_processing]
status: ongoing
edited: 2021-10-21
---

# How to Parallelize with Verstack
Multicore is a tool from [[verstack|Verstack]] that executes a function in parallel.

Here's a [[python|Python]] code example:
```python
data = range(0,10000000)

print('engaging')

def exponential(n):
    # Real hard work here
    return n**2

def execute_func_using_verstack(func,iterable):
    from verstack import Multicore
    print('working')
    worker = Multicore()
    result = worker.execute(func, iterable)

if __name__ == '__main__':
    print('starting')
    execute_func_using_verstack(exponential, data)
```
Execute time for this results in 1.5 seconds.

If I were to do the same normally (without parallel processing);
```python
data = range(0,10000000)

def exponential(n):
    # Real hard work here
    return n**2

if __name__ == '__main__':
    for x in data:
        exponential(x)
```
This takes about 4 seconds.

So, verstack multicore works.

BUT...

## Issues
Multicore behaves a bit weirdly on __Windows__, where codes in the python file gets executed as many times as the number of workers. Details [here](https://github.com/DanilZherebtsov/verstack/issues/9). Note that this issue does not happen on Linux based systems and on OSX.

## My Thoughts
Would I use this? Not really. But it's worth checking out, seeing how this package is rather new and maintained by a few.

## References
- https://danilzherebtsov.medium.com/parallelise-like-a-boss-with-a-single-line-of-code-in-python-30af0d640511