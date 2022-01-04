---
aliases: [Random ID Generator, What is Random in CS]
tags: [python, code, example, HOW-TO, computer_science, WHAT-IS]
status: complete
edited: 2022-01-04
---

# Random ID Generator
Scrapped from [here](https://stackoverflow.com/a/2257449/10570582)

One Liner v1
```python
''.join(random.choice(string.ascii_uppercase + string.digits) for _ in range(N))
```

One Liner v2
```python
''.join(random.choices(string.ascii_uppercase + string.digits, k=N))
```

One Liner v3 (secure-ish)
```python
''.join(random.SystemRandom().choice(string.ascii_uppercase + string.digits) for _ in range(N))
```

In details, as a function
```python
>>> import string
>>> import random
>>> def id_generator(size=6, chars=string.ascii_uppercase + string.digits):
...    return ''.join(random.choice(chars) for _ in range(size))
...
>>> id_generator()
'G5G74W'
>>> id_generator(3, "6793YUIO")
'Y3U'
```

## Using Secrets Library
To be cryptographically secure, it is recommended to use python's built-in library [secrets](https://docs.python.org/3/library/secrets.html) for py36 and above.

```python
''.join(secrets.choice(string.ascii_uppercase + string.digits) for _ in range(N))
```


# Random in Computer Science
In [[computer_science|Computer Science]], random is divided into two categories,
1. True Random
2. Pseudo-Random

More on this topic [here](https://en.wikipedia.org/wiki/Random_number_generation)

## True Random
It's actually nearly impossible to be __ABSOLUTELY__ random, but there are some phenomena that we consider to be random enough that we can call them _True Random_.
- Thermal Noise
- Photoelectric Effect
- Quantum phenomena

True Random is unpredictable _for as long as_ an equation governing such phenomena is not known or not computable.

Often times, True Random is generated with hardware, i.e. _HRNG (Hardware Random Number Generator)_. Such devices are also called _TRNG (True Random Number Generator)_.

The only times when True Random is _truly_ needed is when something needs to be cryptographically secure (passwords, sensitive information), or unpredictable (test answers, lottery).

More info at this [wiki](https://en.wikipedia.org/wiki/Hardware_random_number_generator)

## Pseudo-Random
Most of the times, True Random isn't necessary. As long as something is random enough, it'll do. _PRNG (Pseudo-Random Number Generator)_, also known as _DRBG (Deterministic Random Bit Generator)_, is an algorithm that generates a sequence of random numbers. It is called _Deterministic_ because the generated sequence is completely determined by an initial value (referred to as _seed_).

Basically, PRNG is a software that mimics randomness.

PRNG has come a long way to be very close to random. __SHA-256__ is known to be cryptographically secure (that's why it's used for encryption).

Beware though, because PRNG can never be truly random.

John von Neumann #todo cautioned about PRNG, saying "anyone who considers artihmetical methods of producing random digits is, of course, in a state of sin".

More info at this [wiki](https://en.wikipedia.org/wiki/Pseudorandom_number_generator)