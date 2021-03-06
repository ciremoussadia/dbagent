# 2.2.1 - 2020/10/27

* Add a Typecheck utility viewpoint.

# 2.2.0 - 2020/10/27

* Improve logging: exposing now the `DBAGENT_LOGLEVEL`
  and `DBAGENT_LOGSQL` environment variables.

* Add support for (optional) Bmg viewpoints in db:flush,
  through a viewpoints/ folder in root directory

# 2.1.1 - 2020/09/17

* Fix Dockerfile to listen to 0.0.0.0 and not only on
  127.0.0.1. The fix has been backported to 2.0 and 2.1
  docker images.

# 2.1.0 - 2020/09/17

* db:restore now support an optional argument to list the
  candidate backup files, based on a word:

      rake db:restore[production]

* db:dependencies[table] lists all tables that depends on
  the given table, or of a table that depends on it, based
  on foreign keys.

# 2.0.0 - 2020/09/17

* The default environment variables are set to connect to
  the suppliers-and-parts database on localhost, using a
  dbagent/dbagent user/password pair. This aims at making
  hacking on dbagent itself easier. It should not break
  existing deployments having all environment variables
  properly set.

* Migrated out of ruby passenger, to simply use ruby 2.7
  and rackup on port 80. This should not break anything, as
  the public interface did not change (rake commands, web
  services).

* The backups/ and schema/ folders are now part of the
  base images (as empty folders). This might break an
  existing Dockerfile that mkdir them without the -p flag.

* Since Sequel dependency has been upgraded to ">= 5", some
  migrations may be broken (if they use the fact that the `up`
  method received the db as argument). Simply use `self`
  instead of `db` and all should be fine.

# 1.x

DbAgent first version.
