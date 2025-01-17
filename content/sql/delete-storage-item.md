---
title: "Delete Storage Item"
description: Delete items in Storage using SQL
author: zernonia
github: https://github.com/zernonia
reference:
  - https://github.com/supabase/supabase/discussions/3124
---

The storage schema has bucket and objects table for you to query.
The following command let you see all the items in the storage, and the table structure:

```sql
select * from storage.objects
```

Each row has it's own bucket_id and name, which could help you identify which image URL to remove.
So, in your postgres function, maybe you can do this in case of an exception.

```sql
delete from storage.objects where bucket_id = 'products' and name = 'testing.png'
```

If you afraid this only remove the entry from the table, and doesn't actually free up the Storage space, you can check Storage space at Home, before insert image, after insert the image, finally after the query that remove the image.

You will see the Storage space is the same as before inserting the image.
