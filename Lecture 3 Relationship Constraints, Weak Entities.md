# Lecture 3: Relationship Constraints, Weak Entities and Mapping (Steps 1-2)

<aside>
🎯

**Exam focus:** no item in this lecture was marked MCQ or mid-term, but the mapping steps lead into the mid-term-marked Step 7 in Lecture 4. 

</aside>

## Constraints on Relationship Types

Two constraints: the **cardinality ratio** and the **existence dependency constraint**.

### 1. Cardinality ratio

The **maximum participation**: how many entities of A can be associated with B.

**Example:** Mother 1 — HAS — N Daughter. Each daughter has **one** mother; a mother can have a **maximum of N** daughters.

| Ratio | Example | Reading |
| --- | --- | --- |
| **1:1** | EMP MANAGES DEPT | One employee matched with one department, and vice versa |
| **1:N** or **N:1** | EMP WORKS_FOR DEPT | Each employee works for one department; a department has many employees. Take the **max** from each side, so this is **N:1** (EMP : DEPT) |
| **M:N** | EMP WORKS_ON PROJECT | An employee can work on many projects, and a project has many employees |

### 2. Existence dependency constraint (participation)

| Participation | Meaning | Drawn as |
| --- | --- | --- |
| **Zero** (partial) | Optional, **not** existence-dependent | **One line** |
| **One or more** (total) | Mandatory participation, **existence-dependent** | **Two lines** |

## Attributes on Relationships

Some attributes belong to a **combination of entities**, not to one entity. Example: **Hours per week** for WORKS_ON (employee + project). They are drawn on the relationship (the diamond) itself, not on the entities.

## Weak Entity Types

- An entity type that **does not have a key attribute** (drawn as a double rectangle).
- It must participate in a relationship with another entity type called the **identifying (owner) entity**, through an **identifying relationship** (double diamond).
- It has a **partial key** (dashed underline) that is combined with the key of the owner to identify its entities.
- **Example:** EMP — identifying relationship — DEPENDENT, where the dependent's name is the partial key.

| Extra symbols | Meaning |
| --- | --- |
| Double rectangle | Weak entity type |
| Double diamond | Identifying relationship |
| Dashed underline | Partial key |
| Double line | Total (mandatory) participation |

## ER-to-Relational Mapping

The question: **how does the schema look?** We convert an ER diagram into relations (tables) in **7 steps**. This lecture covers Steps 1 and 2; Lecture 4 covers Steps 3 to 7. Remember that an n-ary relationship is not the same as a binary one.

### Step 1: regular (strong) entity types

- Create one relation per entity type. It includes **all simple attributes** (the table headers).
- For a **composite** attribute, include only its **simple components**, for example Name becomes Fname, Minit, Lname.
- Choose **one of the key attributes** as the primary key.
- Example: EMPLOYEE(Fname, Minit, Lname, Ssn, Bdate, Sex), with Ssn as primary key.

### Step 2: weak entity types

- Create a relation for each weak entity type.
- The **primary key of the owner** is added to it as a **foreign key**, and we draw reference arrows to the owner's primary key.
- The primary key is the **owner's primary key + the partial key**, for example (SSN + name).
- If more than one attribute is underlined in the table, it does **not** mean each one is a primary key on its own. Together they form **one composite key**.

```
DEPENDENT(Ssn, Dependent_name, ...)    PK: (Ssn, Dependent_name)   FK: Ssn -> EMPLOYEE
```

## Quick Practice

- 1. What does a double line between an entity and a relationship mean?
    
    **Mandatory (total) participation**, so the entity is existence-dependent.
    
- 2. What is the primary key of a weak entity's relation?
    
    The **owner's primary key + the partial key**, for example (SSN, dependent name).
    
- 3. What does cardinality ratio measure?
    
    The **maximum participation**: how many entities of A can be associated with B (1:1, 1:N, N:1, M:N).