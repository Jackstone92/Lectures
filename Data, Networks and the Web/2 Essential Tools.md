# Essential Tools

---

# GitLab: What is it?
**GIT** - open source distributed *version control system*  
**GITLAB** - application for *git repository management*  
**SSH (Secure Shell)** - an encrypted network protocol which allows secure access to a remote computer  

## Why use it?
**Essential** in most programming professions for...  
- Developing different parts of application in parallel
- Version management
- Not losing/duplicating stuff
- Collaboration
- Sharing!

## How does it work?
- Project owner **initialises** a git '**repo**' (repository) for a code project
- A **remote** version of the repo may be hosted on the internet
- Permitted users can '**clone**' the remote repo to work on it
- When a user works on a file, they tell Git to **track** it
- When they finish working on it, they '**commit**' their changes
- Git records details about the changes. Each commit (or revision) is given a unique reference (SHA-1 hash)
- User may '**push**' their revisions back to the origin (the remote repo that they originally cloned)
> https://git-scm.com/

## Essential git commands (in sequence):
- **Pull** - to get any new revisions
- **Add** - to start tracking a file
- **Commit** - to commit a revision
- **Pull** - in case anything has changed since the last pull!
  - **Merge** any changes (if applicable)
  - **Commit** the result of a merge (if applicable)
- **Push** - to push your revisions to the remote

# JSON
- Objects are things

```javascript
blog = [
  {
    "timestamp": 1507216999,
    "text": "How do you like those apples?",
    "likes": 130,
    "username": "garry987"
  },
  {
    "timestamp": 1507224587,
    "text": "Nobody likes me",
    "likes": 0,
    "username": "tommy111"
  }
];
```
- Objects have properties
  - "timestamp"
  - "text"
  - "likes"
  - "username"

- Nested objects

```javascript
blog = [
  {
    "timestamp": 1507216999,
    "text": "How do you like those apples?",
    "likes": 130,
    "user": {
      "username": "garry987",
      "hobbies": ["golf","billiards"],
      "pets": {
        "name": "rex",
        "type": "cat"
      }
    }
  }
];
```

- The objects are **related**
  - Should every post by garry987 include details about his cat?

# Relational Databases
- In a relational database, each type of object is represented by a **table**
- **Columns** in the tables represent the object **fields** (aka the **properties** of the object)
- Each **row** or **record** represents a unique instance of an object
- Relationships can be defined between **entities** in the **schema**
