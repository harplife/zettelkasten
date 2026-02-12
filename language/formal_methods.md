# Formal Methods

#define [Formal Science](https://en.wikipedia.org/wiki/Formal_science) is a branch of science studying disciplines concerned with abstract structures described by *formal systems*.

#define A [Formal System](https://en.wikipedia.org/wiki/Formal_system) (Deductive System) is an abstract structure and formalization of an axiomatic system used for deducing, using rules of inference, theorems from axioms.
- [List of formal systems](https://en.wikipedia.org/wiki/List_of_formal_systems)

#define A [Formal Language](https://en.wikipedia.org/wiki/Formal_language) is a language that uses a set of strings whose symbols are taken from a specific alphabet, and operations used to form sentences from them.
- Like languages in linguistics, formal languages generally have syntax and semantics.

#define [Formal Methods](https://en.wikipedia.org/wiki/Formal_methods) are mathematical techniques for specifying, modeling, and verifying software systems to ensure correctness, safety, and reliability.
- The point is to use logic and mathematics (as opposed to informal reasoning) to prove correctness of a system.
- #define In theoretical computer science, an algorithm is [correct](<https://en.wikipedia.org/wiki/Correctness_(computer_science)>) with respect to a specification if it behaves as specified.
- Properties of an execution of a computer program have long been formulated by giving [safety and liveness properties](https://en.wikipedia.org/wiki/Safety_and_liveness_properties).

Formal methods employ a variety of theoretical computer science fundamentals, including :
- Logic calculi
- Formal languages
- Automata theory
- Control theory
- Program semantics
- Type systems
- Type Theory

Most formal methods include three core parts :
1. Formal Specification
2. Modeling
3. Verification

---
#define [Formal Specification](https://en.wikipedia.org/wiki/Formal_specification) is a precise mathematical description of system behavior.
- It is written in logic, set theory, type theory, or algebra
- It defines required properties like correctness, safety, or consistency

A good specification must have some of the following attributes :
- Adequate
- Internally consistent
- Unambiguous
- Complete
- Satisfied Minimal

A good specification will have :
- Constructability, manageability, and evolvability
- Usability
- Communicability
- Powerful and efficient analysis

Implementations of formal specifications will differ depending on :
- What kind of system they are attempting to model
- How they are applied
- At what point in the software life cycle they have been introduced

Specification paradigms :
- History-based specification
- State-based specification
- Transition-based specification
- Functional specification
- Operational specification
- Multi-paradigm languages

#define A [Specification Language](https://en.wikipedia.org/wiki/Specification_language) is a formal language in computer science used during systems analysis, requirements analysis, and systems design to describe a system at a much higher level than a programming language.
- An important use of specification languages is enabling the creation of proofs of program correctness.

Specification languages include :
- VDM
- Z notation
- TLA+


<center>. . .</center>

#example Say there's a function that sorts a list. Instead of informally saying "The function sorts a list", I can specify that "For all lists `L`, `sorted(L') AND permutation(L, L')`". This clearly indicates that the output list is sorted and the output list contains exactly the same elements as the input; this way, correctness has a precise meaning.


---
#define A [Mathematical Model](https://en.wikipedia.org/wiki/Mathematical_model) is an abstract description of a concrete system using mathematical concepts and language. The process of developing a mathematical model is termed **Mathematical Modeling**.

Modeling is an abstract representation of the system, such as :
- State machines
- Transition systems
- Logical formulas
- Algebraic models

<center>. . .</center>

#example A traffic light system might be modeled as :

```mathematica
State ∈ {Red, Green, Yellow}
Transitions:
Red → Green
Green → Yellow
Yellow → Red
```

With this model, safety properties can then be reasoned.

---
#define [Formal Verification](https://en.wikipedia.org/wiki/Formal_verification) is the act of proving the correctness of a system with respect to a certain formal specification (or property).
- The verification of these systems is done by ensuring the existence of a formal proof of a mathematical model of the system.


## Variations of Formal Methods

Formal methods differ mainly in how verification is performed. Variations of formal methods include :
- Theorem Proving (Deductive Verification)
- Model Checking
- Type Systems (Lightweight Formal Methods)
- Static Analysis
- Abstract Interpretation

---
**Theorem Proving** involves using mathematical proofs and proof tools. Examples :
- Coq
- Lean
- Isabelle

They are very powerful but labor-intensive.

---
**Model Checking** involves exploring all possible system states and finding counter-examples if properties fail. Examples :
- TLA+
- SPIN
- NuSMV
- Alloy

They are highly automated and excellent for concurrency & distributed systems. However, not great for large systems (state explosion).

---
**Type Systems** encode correctness constraints in types which are checked at compile time. Examples :
- Rust ownership system
- Haskell type system

They are practical and widely used, tend to be lightweight, and prevents many classes of bugs.

---
**Static Analysis** involves analyzing code without executing it and checking for violations of rules or properties. Examples :
- Null pointer detection
- Data race analysis
- Security property checks

Although it scales well, it is usually conservative (may give false positives).

---
Abstract Interpretation involves approximating program behavior mathematically. It is used for scalable static analysis, and common in safety-critical systems and compiler optimizations.


## Vienna Development Method

#define The [Vienna Development Method](https://en.wikipedia.org/wiki/Vienna_Development_Method) (VDM) is one of the longest-established formal methods for the development of computer-based systems, originating from IBM Laboratory Vienna in the 1970s.
