# Lecture 2: ER Model, Attributes and Relationship Types

<aside>
🎯

**Exam focus in this lecture**

- 📝 **ER models**: marked **mid-term** (and project)
- 🔴 **Types of attributes**: marked **MCQ**
- 🔴 **Relationship types** (including degree): marked **MCQ**
</aside>

## 📝 ER Models

**ER = Entity-Relationship.** In the **conceptual data model** we use ER to model the database.

- **Entity type:** each title or schema instance, for example EMPLOYEES or DEPARTMENTS.
- **Entity:** a specific object or thing, for example *Mohamed is an Employee*. An entity is a member of an entity type.
- **Attributes:** describe the entity types (for example Name, ID). Each entity has a value for each attribute, and each attribute has a **value set** (its data type).

## ER Notation

| Element | Symbol |
| --- | --- |
| Entity type | Rectangle |
| Attribute | Oval |
| Key attribute | Oval with the name **underlined** |
| Composite attribute | Oval with more ovals attached for its components |
| Multi-valued attribute | **Double oval** (oval inside an oval) |
| Derived attribute | **Dashed** oval |
| Relationship type | Diamond |

## 🔴 Types of Attributes (MCQ)

| Pair | First type | Second type |
| --- | --- | --- |
| **Simple vs composite** | **Simple (atomic):** a single atomic value, for example ID, age | **Composite:** several components, for example Name = (first name, last name). It may be a **hierarchy**: Address → Street and Flat, and Street → Name and Number. |
| **Single-valued vs multi-valued** | **Single-valued:** only ONE value, for example Age: 18 | **Multi-valued:** many values, for example Car color: Yellow, Orange |
| **Stored vs derived** | **Stored:** values entered by the user | **Derived:** computed from stored values, for example Age from Date of birth |

### NULL values

1. **Not applicable:** the entity has no applicable value for that attribute.
2. **Unknown:** we do not know the value for that particular entity.

### Key attributes

- Must have a **unique value**, like SSN or ID.
- Every entity type needs **at least ONE** key attribute.
- Drawn as an oval with a line under the name.
- Using it makes data retrieval much easier.

## 🔴 Relationship Types (MCQ)

- **Relationship:** relates **two or more entities** together.
- **Relationship type:** relationships of the **same type** grouped together.
- **Relationship degree:** the **number of entity types** in it.

| Degree | Name | Example |
| --- | --- | --- |
| 2 entity types | **Binary** | DEPT works on EMP |
| 3 entity types | **Ternary** | One relationship R linking entities 1, 2 and 3 |
| n entity types | **N-ary** | Needs its own mapping rule (Lecture 4, Step 7) |

## Quick Practice

- 1. What shape represents a derived attribute?
    
    A **dashed oval**. (Multi-valued is a double oval, key is an underlined oval.)
    
- 2. What is a relationship among three entity types called?
    
    **Ternary** (degree 3). Degree is the number of entity types.
    
- 3. Which attribute type is Age when it is calculated from Date of birth?
    
    **Derived** (and the Date of birth it comes from is a stored attribute).