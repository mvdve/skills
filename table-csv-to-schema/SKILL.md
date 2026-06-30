---
name: table-csv-to-schema
description: Create an Effect.ts schema from a CSV MSSQL table definition.
---

# Table CSV to Schema

Use this skill to create an Effect.ts schema from a CSV MSSQL table definition.

## Rules

1. CSV column A is the table column name.
2. CSV column B is the table column type.
3. CSV column C defines whether the column can be null where checked it can be null.
4. Use `s.optionalWith(<type>, {nullable: true})` when a colum can be null.
5. Ignore timestamp and sysguid columns.

## Type mapping (type from CSV to Effect.ts schema type)
- int = s.Int
- smallint = s.Int
- tinyint = s.Int, add comment: `@todo: check if boolean`
- float = s.Number
- varchar(x) = s.String
- uniqueidentifier = s.String
- char(x) = s.transform(s.String, s.String, {
  decode: (v) => v.trim(),
  encode: (v) => v.padEnd(x, ' '),
}), add comment: `@todo: check for padStart of padEnd`
- bit = s.Boolean
- datetime = s.DateFromSelf
- varbinary(x) = s.Uint8ArrayFromSelf
