# Prisma migrate bug

This repository just describes migration bug in prisma 2.23.0 for mysql database.

# The problem

Upon making simple change in my project and trying to perform migration on my deployment server I found out prisma generated incorrect table name.
2nd migration file should be contain "Player" table (as in initial file), however "player" is present.

Mysql version present on my server:

`mysql Ver 14.14 Distrib 5.7.34, for Linux (x86_64) using EditLine wrapper`

# Steps to reproduce

Do the following:

- `npx prisma init`
- Create simple table starting with uppercase and run `npx prisma migrate dev --name init`
- Change some field in table and run `npx prisma migrate dev --name init2`
- Copy repository to deployment machine and run `npx prisma migrate deploy`
