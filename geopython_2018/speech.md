# PostgreSQL / PostGIS migrations using Python

## Intro
Good afternoon. Welcome to my presentation about Postgres migrations using Python.

## Who am I?
My name is Mario Baranzini.
I work as developer (mostly on Python and Java), consultant, and teacher in the GIS field. I come from the Italian speaking part of Switzerland (so sorry for my English...).

## OpenGIS.ch
I work in a small company called OpenGIS.ch. We are specialized on open-source GIS and web development for small and medium businessess.

## Abstract
Today I am here to talk to you about database migration and evolution. I want to show to you how we manage database evolution in two open-source projects related to QGIS: QWAT and QGEP. Two projects for manage water networks. One for drinkable water and the other for waste water.

But let's do a jump back for a second

## Waterfall processes
Some time ago, when the waterfall process was the common way to develop software, we tended to define the db model at the beginning of development and we tried in every way to no longer modify it.

## Iterative processes
Then, over time, other iterative development methodologies have made their way, where the whole process is repeated in more or less long iterations.
- This involves the design of new features and sometimes the refactoring of existing ones with consequent evolutions of the code and the databse...

## Code evolution
For code evolution's management, methodologies have spread widely and are universally accepted. One in all in the open-source area, is linked to the git software, which pushes the developer to work on a copy of the code, test the changes locally, and then merge the changes in the production code and push it back in the production repository.

## DB evolution
In the database area, however, often changes are managed in a more informal way even if there are recognized practices.
Some of the most important and useful practices, which often use a similar approach to what happens with the code, are:
- the use of local db instances
- the use of migration files for each modification to the db
- the versioning of each db artefact
- CI

## Local DB instances
As happens with the code, each developer works on a local copy of the database. This implies that the local database generation must be simple and automated via scripts. Docker or similar tools are a big help for this.

## Migration (delta) files
Every change made by a developer on the database must be contained in a delta file. A delta file is usually an SQL script that contains the statements to change the database.

## Version control
Every db artefacts (generation script, delta file, data dump, db specification, ...) is version controlled (e.g. with git).

## CI
C.I. stands for Continuous Integration and is referred to a set of techniques and tools to automatically build our code (i.e. our db scripts), execute integration tests, and release the result, ready to be used in a product.

## How to manage all this
The simplest and safest way to handle these practices is to use a so-called migration tool. There are several migration tools available e.g. Flyway-db or Liquibase.

## PUM
And there is PUM (Postgres Upgrades Manager).
As mentioned earlier, some time ago we wanted to apply these practices in two Opensource projects (QWAT and QGEP). We wanted a tool specific for PostgreSQL and PostGIS, and above all, we wanted to integrate the tool into the already existing development process of QWAT and QGEP databases, which are based on the use of SQL files, but also Python scripts.
So we created PUM. PUM was greatly inspired by the existing migration tools and is very simple and easy to use, adapt and extend.

## What does PUM?
Pum is a Python program that can be used via command line or called directly from another Python program.

Pum permits the followings operations on Postgres databases:
- check the differences between two databases
- create and restore a backup (dump file) of a database
- upgrade a database applying delta files
and some other useful operations like testing a migration before applying it.

## Check
The check command compares 2 databases and shows the differences. It compares the following elements and tells if they are different:
- tables
- columns
- constraints
- views
- sequences
- indexes
- triggers
- functions
- rules
It's possible to ignore one or more of these elements.

## Upgrade
The upgrade command is used to upgrade an existing database using SQL or Python delta files. The command applies one or more delta files to an existing database and stores in a table the information about the applied deltas.

## Test-and-upgrade
The test-and-upgrade command does the following steps:
- creates a dump of the production db
- restores the db dump into a test db
- applies the delta files found in the delta directories to the test db.
- checks if there are differences between the test db and a comparison db
- if no significant differences are found, after confirmation, applies the delta files to the production db.

## Delta files
As said before, a delta file can be a SQL file containing one or more SQL statements or a Python module containing a class that is a subclass of DeltaPy.

There are different kind of delta files like the pre-all and the post-all that are executed on each migration.

## Use and contribute
PUM is installable using pip install pum.
PUM sources are released under GPL Licence and are available at https://github.com/opengisch/pum Feel free to modify and propose your contributions.

## Thank you
Thank you for your attention.
