@title[Title]

### Postgres/PostGIS <span class="gold">migrations</span> using Python
#### <span class="gold">PUMp your db with PUM</span>
<br>
<br>
<span class="byline">Geopython 2018, Basel - May 8, 2018</span>

Note:
Good afternoon. Welcome to my presentation about Postgres migrations using Python.

---
@title[Who am I?]

TODO Who am I?

Note:
My name is Mario Baranzini.
I work as developer (mostly on Python and Java), consultant, and teacher in the GIS field. I come from the Italian speaking part of Switzerland (so sorry for my English...).

---
@title[OpenGIS.ch]

TODO openGIS.ch

Note:
I work in a small company called OpenGIS.ch. We are specialized on open-source GIS and web development for small and medium businessess.

---
@title[Abstract]
## Database migration and evolution

Note:
Today I am here to talk to you about database migration and evolution. I want to show to you how we manage database evolution in two open-source projects related to QGIS: QWAT and QGEP. Two projects for manage water networks. One for drinkable water and the other for waste water.

But let's do a jump back for a second

---
@title[Waterfall]
TODO schema waterfall

Note:
Some time ago, when the waterfall process was the common way to develop software, we tended to define the db model at the beginning of development and we tried in every way to no longer modify it.

---
@title[Iterative]
TODO schema iterative

Note:
Then, over time, other iterative development methodologies have made their way, where the whole process is repeated in more or less long iterations.
- This involves the design of new features and sometimes the refactoring of existing ones with consequent evolution of the code and the database...

---
@title[Code evolution]
## Code evolution

Note:
For code evolution's management, methodologies have spread widely and are universally accepted. One in all in the open-source area, is linked to the git software, which pushes the developer to work on a copy of the code, test the changes locally, and then merge the changes in the production code and push it back in the production repository.

---
@title[DB evolution]
## DB evolution
- local DB instances
- migration files
- versioning
- C.I.

Note:
In the database area, however, often changes are managed in a more informal way even if there are recognized practices.
Some of the most important and useful practices, which often use a similar approach to what happens with the code, are:
- the use of local db instances
- the use of migration files for each modification to the db
- the versioning of each db artefact
- CI
