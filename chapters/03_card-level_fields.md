[< Previous: 2. General Structure](02_general_structure.md) | [Back to TOC](../README.md) (main documentation) | [Next: 4. Face-Level Fields](04_face-level_fields.md)

# 3. Card-Level Fields

Every card definition file in MCD must return a table with these top-level fields at the root level:

| Field    | Required | Type   | Description                                |
|----------|----------|--------|--------------------------------------------|
| `id`     | Yes      | string | Unique ID of the physical or printed card  |
| `layout` | Yes      | string | Card layout type (`normal`, `split`, etc.) |
| `faces`  | Yes      | array  | Array of one or more card face definitions |

The `faces` array must contain at least one face object, each of which is structured as described in Chapter 4.

---

[< Previous: 2. General Structure](02_general_structure.md) | [Back to TOC](../README.md) (main documentation) | [Next: 4. Face-Level Fields](04_face-level_fields.md)
