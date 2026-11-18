# Lecture 4: ER-to-Relational Mapping (Steps 3-7)

<aside>
🎯

**Exam focus in this lecture**

- 📝 **Step 7, mapping n-ary relationship types**: marked **mid-term**
- ✍️ In-class exercise "Edit assumptions and update schema": worked solution below
</aside>

## Mapping Cheat Sheet (all 7 steps)

Steps 1 and 2 are in Lecture 3.

| Step | ER construct | What to do |
| --- | --- | --- |
| **1** | Regular (strong) entity | One relation with all simple attributes; choose a key as primary key |
| **2** | Weak entity | New relation; add the owner's primary key as a foreign key; primary key = owner's key + partial key |
| **3** | 1:1 relationship | Three options: foreign key, merged relation, or cross-reference table |
| **4** | 1:N or N:1 relationship | Put the foreign key on the **N** side |
| **5** | M:N relationship | **New table** holding both primary keys |
| **6** | Multi-valued attribute | New table with the attribute and the owner's key |
| **7** 📝 | N-ary relationship (3 or more) | **New table** with the N primary keys |

### Step 3: 1:1 relationship types

Three options. Use any of them.

1. **Foreign key approach:** add the key of one entity as an attribute in the other.
    - You can add it to either entity type: add the column to side 1 and arrow it to side 2, or vice versa.
    - Attributes on the diamond go to the side where you add the column.
    - It is best to add the column where the entity has **total participation** (double line).
2. **Merged relation:** use **only when both entities have total participation**. Represent the two entities in **ONE table** and take one primary key for it.
3. **Cross-reference (relationship) table:** make a new table made of the primary keys of each entity, with arrows to the original keys and entities.

### Step 4: 1:N (or N:1) relationship types

- Add the column (the primary key) to the **"many" (N) entity** and arrow it to the primary key of the **"1" entity**.
- Attributes on the diamond are added to the **N** entity type.
- Rule of thumb: whatever you add, you take it **from the other entity**.

### Step 5: M:N relationship types

- You **must** make a **new table**, named after the relationship (for example WORKS_ON).
- Its columns are the **two primary keys**, one for each entity type (for example SSN and PROJ_ID), with arrows to the original tables.
- Attributes on the relationship (like Hours) go in this new table.

### Step 6: multi-valued attributes

- Create a **new table** for that attribute.
- Add the **primary key of the owner entity**.
- The primary key is composite: **partial key + primary key**.
- Example: DEPT has a multi-valued Location, so DEPT_LOC(DepID, Loc).

### 📝 Step 7: n-ary relationship types (mid-term)

- **Ternary** example: entities 1, 2 and 3 connected by one relationship R.
- Create **a new table with the N primary keys**, one from each participating entity, and draw arrows to the owner entities.

## Worked Example (in-class exercise)

**Task:** start from EMP(SSN, name, depID) and DEPT(DID, name, loc). Edit the assumptions and update the schema.

1. Name is split into Fname and Lname (composite attribute).
2. Location is multi-valued.
3. Many-to-many: an employee can work in many departments.

Resulting schema:

```
EMP(SSN, Fname, Lname)               PK: SSN
DEPT(DID, Name)                      PK: DID
DEPT_LOC(DID, Loc)                   PK: (DID, Loc)   FK: DID -> DEPT
WORKS_IN(SSN, DID)                   PK: (SSN, DID)   FK: SSN -> EMP, DID -> DEPT
```

<aside>
💡

depID is removed from EMP because the M:N relationship now lives in its own table (Step 5), and Location moves to DEPT_LOC (Step 6).

</aside>

<aside>
➡️

**Next up:** Chapter 4, Enhanced Entity-Relationship (EER) model. Notes not taken yet.

</aside>

## Quick Practice

- 1. How is an M:N relationship mapped?
    
    A **new table** named after the relationship, holding **both primary keys** (as a composite key) plus any relationship attributes.
    
- 2. In a 1:N relationship, which side gets the foreign key?
    
    The **N** (many) side, pointing to the primary key of the 1 side.
    
- 3. How is a ternary relationship mapped?
    
    A **new table** containing the **3 primary keys** (one per entity), with arrows to the owner entities.
    
- 4. When can a 1:1 relationship use the merged-table option?
    
    Only when **both entities have total participation**. Both go in one table with one primary key.