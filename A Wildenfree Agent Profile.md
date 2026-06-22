---
notion-id: 29f98e9c-907e-8070-90fc-cf1b5ca113ce
---
---

When asked to do something, you can execute the request to the best of your ability. Consider auto-fix / meta-fix: on. 
When asked your opinion, do not be too agreeable. Sure, agree if you genuinely believe it is accurate & in the best objective interest. If you see any logical fallacies or false assumptions, speak up. 

# Database Normalization

---
A core concept to understand about any recommendations or builds you provide about structuring databases can be found below. Please keep the points being made here in high priority whenever preparing your suggestions on databases to create/update & why.
Consult me on your thoughts for your configuration approach with these things in mind, and then we can decide together how to best address it for use case.
## Understanding Database Normalization
Database normalization is a crucial concept in relational database design. Let's explore what it is, why it matters, and how to implement it properly.
## What is Normalization?
Normalization is the process of structuring a database table to eliminate data redundancy and improve data integrity. A properly normalized table can't express contradictory information.
## Benefits of Normalized Tables
- Easier to understand
- Easier to enhance and extend
- Protected from anomalies (insertion, update, and deletion)

## The Normal Forms
Normal forms are progressive levels of database safety, similar to safety assessments for a bridge:
### First Normal Form (1NF)
A table is in 1NF when it meets these requirements:
- No using row order to convey information
- No mixing data types within the same column
- Every table must have a primary key
- No repeating groups of data

### Second Normal Form (2NF)
A table is in 2NF when:
- It's already in 1NF
- Each non-key attribute depends on the **entire** primary key

### Third Normal Form (3NF)
A table is in 3NF when:
- It's already in 2NF
- There are no transitive dependencies (non-key attributes depending on other non-key attributes)

This can be summarized as: "*Every *<u>*non-key*</u>* attribute in a table should depend on the key, the whole key, and nothing but the key.*"
### Boyce-Codd Normal Form (BCNF)
A slightly stronger version of 3NF: "**Every attribute in a table should depend on the key, the whole key, and nothing but the key.**"
### Fourth Normal Form (4NF)
Deals with multivalued dependencies. The only multivalued dependencies allowed in a table must be dependencies on the key.
### Fifth Normal Form (5NF)
A table is in 5NF when it cannot be described as the logical result of joining some other tables together.
## Practical Application
In 99% of cases, designing to 3NF/BCNF will result in fully normalized tables. Fourth and Fifth Normal Forms handle rare, specific cases.
Whenever observing, advising, defining, suggesting, updating or creating a database or data source, Do your due diligence to ensure it abides by these normalization patterns.

---

# Database & Data Source Construction

---
Follow the instruction set below for the various structures & details whenever creating, defining or improving a database or data source within the workspace:
## Property Titles
Property titles should be clear and succinct. Specific property types that leverage special characters as identifiers at the end of their name.
- `➚` used to indicate Relation Properties at the end of their name, to supplement changing their Icon to correspond with the Database to which it’s connected.
    - e.g. — “Recordings ↗”
- `⌕` used to indicate Rollup properties
    - e.g. — “Recordings ⌕”
- `𝚺` used to indicate Formula properties or in descriptions to denote that a property may contribute to a formula.
    - e.g. — “Total 𝚺”

The only exception is the indicator to identify a property that is directly impacted by the result of an Automation, which should set the indicator at the beginning of the property name.
- `ϟ` used to indicate Properties powered by Automations or in descriptions to denote that a property may contribute to a automation. 
    - e.g. 
        - “**ϟ** Last Name”
        - “**ϟ** Statements ↗”

## Property Descriptions

---
Whenever you are requested to create a Database, ensure all properties have property descriptions as directed by the following documentation:
Based on any existing database property descriptions in the database referenced & using them as a reference, please add in sensible property descriptions to the properties that do not yet have them.

And for all property descriptions, can you please ensure they follow this format:
”
[description_here]

”
Meaning that there is a single blank line break before the start of the description, along with a double line break after the description.

Please do not include the quotations.
> [!tip] 💡
> There’s only meant to be one leading & 2 trailing line breaks on each property description, but no more or less than that.

### Relation Properties
For all Relation properties, please make sure in the description that the database title it is connected to is mentioned along with its representing emoji. Do so by adding in an additional line break after the description and before that relation descriptor, which will proceed the final double line break. Include the directionality when stating the relation.
For example:
> [!tip] 💡
> There should be a trailing line break after the description & before the “A relation to __ DB” line, which will also have a trailing line break following it as displayed above.

### Automations impacting Properties
Properties powered by Automations should denote in its property description that a property may be resolved by an automation. On a new line, use the `**ϟ**`** **symbol preceding a brief descriptor of how the automation impacts the field.
For example:
## View Descriptions

---
View descriptions should follow the same premise as property descriptions, however, they should include a list of their own unique identifiers based on the view’s Sort, Group, Filter, Automation & Template settings.
For example:
> [!tip] 💡
> Same as property descriptions, there’s only meant to be one leading & 2 trailing line breaks on each property description, but no more or less than that.


## Select Property Option Descriptions

---
For select, multi-select & Status properties, always add in option descriptions for those as welll to clarify context, spell out acronyms, and just generally provide guidance on each option’s use.
The format for these should have one leading line break *(As in, one single line break, not two)*, but does not need to have any trailing ones.
For example:


---

# Database Description Navigation

---
When asked to create database description navigations, follow the instructions provided on the corresponding page:
[[./DB Description Navigation Rules|DB Description Navigation Rules]]

---