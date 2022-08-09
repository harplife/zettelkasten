---
aliases: [TODO Management App, TODO App, Task Management App, Tasks App]
tags: [TODO, management, app, web, project, ideas, python, programming]
status: ongoing
created: 2022-08-09
edited: 2022-08-09
---

# TODO Application Project

## Goal
The goal is to make an application that can help manage TODOs.

The focus will be on Task, Relationship, and Management.

## Task
A **TODO** is a task that needs to be completed, therefore it is a task that needs to be tracked and reminded as necessary.

I will be using the term **TASK** synonymously.

### Types
There are two types of TODOs.
1. Repeating
2. Non-Repeating

A Repeating TODO is a task that needs to be completed repeatedly, at every day, week, or any designated span of time.

A Non-Repeating TODO is a task that needs to be completed only once.

### Metadata
A task includes (but not limited to) the following information:
1. Subject
2. Description
3. Estimated Start/End Date
4. Actual Start/End Date
5. CRUD Date

Additional information for Management:
1. Show on Daily (True/False)
2. Shared to Other Users (True/False)

Added complexity for repeat:
1. Repeat Type (every n day)

Additional information for Sharing:
1. Created By
2. Edited By
3. Tasked To
4. Deleted By

### Check in
Some tasks take over a day to complete. "Checking in" helps tracking whether a task has been looked at recently.

## Note
A **Note** can be attached to Task(s) to extend information about the Task. It speaks for itself.

Although Task itself has "Description" for additional information, a Note can go further by adding details to multiple tasks at once.

It can serve also as a "Warning". For example, a Note can notify the critical change made by a certain Task to the Tasks that may be affected.

## File
A **File** can be attached to Task(s) to extend information, and/or to extend management beyond the scope of the interface.

For example, an Excel file can be attached to a task because it may be better suited for managing a task.

## Relationship
A **Relationship** describes the hierarchy of a task to another.

The relationship can be extended to File-Task, Note-Task, and etc.

### Parent to Child
#### Task to Task
The Relationship between two tasks is Parent-to-Child.
A Parent Task can have multiple Child Tasks. However, a Child Task cannot have multiple Parent Tasks.

This helps breaking down a task into smaller tasks for efficient task handling.
Also, this allows for "Project Management", where the 1st Level Parent Task is essentially the Project.
There is no need to define a task as a project, as it is implied.

If multiple Child Tasks exist under a Parent Task, then it is implied that those Child Tasks are related (siblings).

If multiple Child Tasks are under different Parent Tasks but those Parent Tasks are on same level, then it is also implied that those Child Tasks are related (cousins).

#### Task and others
Task cannot be in Parent-to-Child relationship with Note or File.

### Attachment
#### Note to Task
Note is always an "Attachment" to a Task.

A Note can be attached to multiple Tasks.

Multiple Notes can be attached to a single Task.

#### File to Task
File is always an "Attachment" to a Task.

A File can be attached to multiple Tasks.

Multiple Files can be attached to a single Task.

#### File and Note
File(s) can be attached to a Note. Preferably, it should only be used to provide more detail about the Note.

Note(s) cannot be attached to a File.

### Warning
- Task/Note/File cannot relate to itself
- Task/Note/File cannot relate to duplicated targets

## Management
A **Management** consists of
1. CRUD operations
2. Overview

### CRUD operations
#### Task

#### Note

#### File

### Overview
#### Task Information
Viewing information of a Task.
- [[#Task#Metadata]]
- Parent Task
- List of Child Tasks
- List of Notes
- List of Files
- Check-in Information

#### Daily Tasks
Viewing a list of Tasks that are
1. not completed
2. opted TRUE for SHOW_ON_DAILY
3. (optional) repeat day == today



#### Check in

## ideas
- #todo share_to_child option on any attachment(note/file) may be useful.