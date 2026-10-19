---
name: data-model
description: >
  Decide whether a feature needs a new database table, or should extend an
  existing table or reuse a shared store. Use when a task adds or changes
  database tables, schemas or migrations, or designs storage for a feature, on
  SQLite, D1, Postgres or a similar relational database. Requires a stated
  reason for every new table, keeps durable records apart from disposable data,
  and records owner, readers and writers, retention, backup and restore, and
  rollback for every schema change. Never deletes data or a table without a
  verified backup and explicit owner approval.
---

# data-model

A schema outlives the feature that first needed it.
Every table you add is one more thing to back up, restore, migrate, secure and explain, so the default is to fit new data into what exists.
These rules apply whenever a task adds or changes a table, a column, an index, a trigger or a migration, or plans where a feature's data will live.
They hold for SQLite, D1, Postgres and other relational databases.

This is the storage form of the "Reuse before you write" rule in `design-review` for interface components.

## When to add a table

A new feature is not by itself a reason for a new table.
Add a table only when at least one of these holds:

1. **Distinct entity.** The rows describe a thing the existing tables do not, with its own identity.
2. **Different cardinality or lifecycle.** The data is many-per-row where the existing table is one-per-row, or it is created, changed or removed on a different schedule.
3. **Different rules.** The data needs different access, retention, encryption or recovery rules from the table it would otherwise join.
4. **Keys and constraints.** The data needs keys or constraints an existing table cannot hold cleanly.
   Cleanly means without columns that are empty for most rows, a type column that changes what other columns mean, or a constraint you would have to loosen.

Name the reason that applies in the migration notes or the pull request.
If you cannot name one, do not add the table.

## When to extend or share

When no reason above applies, add columns to the existing table that owns the entity.

Some plumbing recurs in almost every project and should exist once, shared by every feature that needs it:

- reviews before saving, where a change waits for approval before it is applied
- background readers, such as job state, sync cursors and polling checkpoints
- settings and switches
- audit logs

Before you create any of these for a feature, search for the one the project already has and reuse it.
A second approval queue for one feature is the storage version of a copied component: the next fix lands in one and not the other.

A shared store needs a scope column, such as a kind, a feature or an owner id, that tells its users apart.
Every query on it filters by that scope, and its indexes lead with the scope column.
Where the database supports it, enforce per-scope rules with a check constraint, a partial index or a unique key that includes the scope.

## What stays separate

Keep durable records apart from disposable data.

Durable:

- business records and their history
- permissions
- proof of external effects, such as a payment taken, a message sent or an id returned by another service
- recovery data

Disposable:

- drafts
- caches
- logs

Do not mix the two in one table.
They have different retention, backup and deletion rules, and a cache purge must never be able to reach a business record.

## No catch-all tables

Do not use a generic key-value table or a table of JSON documents instead of real columns, keys and constraints.
The database cannot check a foreign key, a type or a required field inside a blob, so every reader has to repeat those checks and one of them will not.
A JSON column is acceptable for a payload the database never filters, joins or constrains, such as a raw response kept as proof.

## What every schema change records

Write these down in the migration file, the pull request or the project's schema docs:

- **Owner:** the feature or person responsible for the data.
- **Readers and writers:** every code path that reads or writes it, including triggers, views, scheduled jobs, scripts, admin tools and agent tools.
- **Retention:** how long rows are kept and what removes them.
- **Backup and restore:** whether the data is in the backup, and how it is restored.
- **Rollback:** how to undo the change, and what data the undo loses.

## Deleting data or tables

Never delete data, drop a column or drop a table without a verified backup and explicit approval from the data owner.
A verified backup is one you have restored or read back and found the rows in.
A backup job that reported success is not verification.

Empty or switched off is not proof that nothing needs the data.
A table can be empty in one environment and full in another, a switched-off feature can be switched back on, and a reader can be a job that runs once a month.

Archive before you delete.
Stop writes, keep the data readable for an agreed period, then drop it only with the owner's approval.

## No target count

There is no right number of tables.
Do not merge tables to reach a lower count, and do not split one to look tidy.
Each table exists because one of the reasons above applies to it, or it does not exist.

## Schema review checklist

Check each item before a schema change is merged, and say which ones do not apply.

- [ ] **Reuse considered.** Existing tables and shared stores were searched, and the notes name the ones checked.
- [ ] **Reason named.** A new table names which reason under "When to add a table" applies.
- [ ] **Keys and constraints.** Primary keys, foreign keys, unique keys, not-null and check constraints express the rules, not application code alone.
- [ ] **Shared stores scoped.** Every query on a shared store filters by its scope, and an index leads with the scope column.
- [ ] **All readers and writers found.** The search covered triggers, views, scheduled jobs, scripts, admin tools and agent tools, not only the feature's own code.
- [ ] **Migration fits the database.** The change stays within what the engine can do in place.
  SQLite and D1 cannot add most constraints with `ALTER TABLE`, so the change is a table rebuild: create the new table, copy, drop the old one and rename.
  In Postgres, a plain `CREATE INDEX` blocks writes for its whole run, so large tables use `CREATE INDEX CONCURRENTLY`.
- [ ] **Data moves are replay-safe.** A copy or backfill can run twice, or resume after a partial failure, without losing or duplicating rows.
  Key it on stable ids and use upserts or `ON CONFLICT` clauses rather than blind inserts.
- [ ] **Backup and restore checked first.** Before any step that drops, rebuilds or rewrites data, a backup was restored or read back.
- [ ] **Change recorded.** Owner, readers and writers, retention, backup and restore, and rollback are written down.
- [ ] **Docs updated.** The project's schema docs and schema map show the change.
