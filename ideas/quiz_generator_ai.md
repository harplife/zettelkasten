---
aliases: [Quiz Generator AI]
tags: [artificial_intellgience, idea, memory, quiz]
status: ongoing
edited: 2021-12-28
---

# Quiz Generator AI
It's an AI that "reads" a document and generates a series of questions pertaining to the document.

It would benefit schools, but I'm more interested in using it for memory consolidation.
The purpose of [[what_is_zettelkasten|Zettelkasten]] is to write notes and create a web of knowledge.
But I feel that it can't serve its purpose if I just forget about old notes,
so a way to "remind" old notes is needed.
A simple random reminder would "kinda" do it, but it isn't enough to stimulate the _retrieve/recall_ part of the brain.
Thus, a quiz based on the notes would help.

## Considerations
### Single Sentence Quiz Generation
#### True/False Question
This would be the first step to building a Quiz AI.
It would take a sentence, and deform it.
For example, if the original sentence is this:
> Newton was studying underneath an apple tree

The AI could deform it like this:
> Newton was studying underneath a banana tree

There, we can treat it like a True/False question.

A better version, an AI that can actually make it into a question.
> Was Newton studying underneath an banana tree?

#### Multiple Choice Question
Select an answer that is correct:
1. Newton was studying underneath a banana tree
2. Newton was eating underneath an apple tree
3. Franklin was studying underneath an apple tree
4. Newton was studying underneath an apple tree

### Multiple Sentence Quiz Generation
#### Fact Extraction
The Quiz AI needs to be able to narrow down important information from multiple sentences.
Often times, although a document is around 1 core idea (topic), it may contain many smaller ideas (facts) that branches from it.

For example, if the original document was like this:
> Newton was studying underneath an apple tree. An apple fell on his head. Newton started thinking about the force that made the apple fall straight down.

Several facts can be derived from the document above,
1. The apple that fell on Newton's head made him think about the force that made the apple fall.
2. Newton was studying underneath an apple tree when he started thinking about the force that made an apple fall.

From there, questions can be made.

More considerations in the future. #todo