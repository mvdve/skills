---
name: ts-import-type-split
description: Enforce TypeScript import style where type-only imports are never combined with value imports, all normal imports come first, and type imports are grouped below with a blank line separation.
---

# TypeScript Import Type Split

Use this skill when editing `.ts` or `.tsx` files and import declarations need to follow a strict type/value split format.

## Rules

1. Never combine type and value imports in one statement.
2. Use `import type { ... } from '...'` for type-only imports.
3. Keep all normal imports together at the top.
4. Insert exactly one blank line between normal imports and type-only imports.
5. Place the `type` keyword immediately after `import`.

## Required Pattern

```ts
import Modal from 'react-modal';
import {useEffect, useState} from 'react';

import type {CSSProperties} from 'react';
```

## Edit Procedure

1. Scan each import statement.
2. If a statement contains both type and value specifiers, split it into separate imports from the same module.
3. Move all `import type` lines below normal imports.
4. Ensure one blank line exists between the two groups.
5. Keep all other code unchanged.
