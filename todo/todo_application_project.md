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

## Note
A **Note** can be attached to Task(s) to extend information about the Task. It speaks for itself.

## File
A **File** can be attached to Task(s) to extend information, and/or to extend management beyond the scope of the interface.

For example, an Excel file can be attached to a task because it may be better suited for managing a task.

## Relationship
A **Relationship** describes the hierarchy of a task to another.

The relationship can be extended to File-Task, Note-Task, and etc.

### Types

#### Task to Task
The Relationship between two tasks is Parent-to-Child.
A Parent Task can have multiple Child Tasks. However, a Child Task cannot have multiple Parent Tasks.

This helps breaking down a task into smaller tasks for efficient task handling.
Also, this allows for "Project Management", where the 1st Level Parent Task is essentially the Project.
There is no need to define a task as a project, as it is implied.

If multiple Child Tasks exist under a Parent Task, then it is implied that those Child Tasks are related (siblings).

If multiple Child Tasks are under different Parent Tasks but those Parent Tasks are on same level, then it is also implied that those Child Tasks are related (cousins).

#### Note to Task
The Relationship between a Note 

#### File to Task

## Management
A **Management** consists of
1. CRUD of tasks and relations

### Types of Management
