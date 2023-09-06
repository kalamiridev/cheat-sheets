## Delete a Postgres User with Dependencies

1. Assign the object ownership from the error detail to another user. For example, to transfer the objects owned by myuser to postgres, run:

```sql
REASSIGN OWNED BY olduser TO newuser;
```

2. Remove the database object connections to the user with:

```sql
DROP OWNED BY olduser;
```

3. At the moment, the user no longer has any dependencies. To drop the user, run:

```sql
DROP USER IF EXISTS olduser;
```

## Delete a Postgres Role

```sql
DROP ROLE oldrole;
```