# ER Symbols Cheat Sheet

<aside>
🎯

Every drawing and symbol from the ER model lectures in one place. The drawings below are an embedded sheet: open it full screen to see it larger. 🔴 marks symbols tied to an MCQ in your notes.

</aside>

[ER symbols, drawn](er_symbols.html)

ER symbols, drawn

## Text Summary (if the drawing does not load)

| Symbol | Shape | Meaning |
| --- | --- | --- |
| **Entity type** | Rectangle | A kind of thing we store data about (EMPLOYEE) |
| **Weak entity type** | Double rectangle | No key of its own; depends on an owner |
| **Attribute** | Oval | A property of an entity |
| **Key attribute** | Oval, name underlined | Unique value (SSN, ID); at least one per entity type |
| **Composite attribute** 🔴 | Oval with ovals attached | Made of parts (Name = Fname + Lname) |
| **Multi-valued attribute** 🔴 | Double oval | Many values (Phone, Car color) |
| **Derived attribute** 🔴 | Dashed oval | Calculated from another (Age from Date of birth) |
| **Partial key** | Oval, dashed underline | Identifies a weak entity together with the owner's key |
| **Relationship type** 🔴 | Diamond | Relates two or more entity types |
| **Identifying relationship** | Double diamond | Links a weak entity to its owner |
| **Partial participation** | Single line | Optional (zero or more); not existence-dependent |
| **Total participation** | Double line | Mandatory (one or more); existence-dependent |
| **Cardinality ratio** | 1, N or M on the line | Maximum number of entities on each side |
| **Attribute on a relationship** | Oval joined to the diamond | Data belonging to the pair (Hours on WORKS_ON) |
| **Binary / ternary** 🔴 | Diamond with 2 or 3 entities | Degree = number of entity types (2, 3, n) |

## Easy Ways to Remember

- **Double means "stronger" or "more":** double rectangle = weak entity, double diamond = identifying relationship, double oval = many values, double line = must participate.
- **Dashed means "not stored directly" or "partial":** dashed oval = derived, dashed underline = partial key.
- **Underline means unique:** solid underline = key attribute.