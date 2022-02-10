# Home Assistant Add-on: Cloudflared

With this Add-on, you can run [NocoDB][nocodb], an open source Airtable
alternative, on your Home Assistant.

NocoDB works by connecting to any relational database and transforming them
into a smart spreadsheet interface! This allows you to build no-code
applications collaboratively with teams. NocoDB currently works with MySQL,
PostgreSQL, Microsoft SQL Server, SQLite, Amazon Aurora & MariaDB databases.

## Installation

The installation of this add-on is pretty straightforward. NocoDB requires a
database to store metadata of spreadsheets views and external databases. If you
run this Add-on without any configuration, it will create a local SQLite in the
'/data' folder. Nevertheless, it is recommended to use the MariaDB Add-on.

Therfore, the following configuration is optional but recommended:

1. MariaDB: It is recommended to run with MariaDB, so install the Add-on
   MariaDB and configure it as described below.
1. Enter the database-details in the Add-on configuration (use the
   'show unused optional configuration options' flag to show the options)

Finally, there are three more steps:

1. Start the Add-on
1. Visit [http://homeassistant:8080](http://homeassistant:8080)
1. Enjoy!

## Configuration

### MariaDB

If you want to use this Add-on with MariaDB, configure an additional database
with logins and rights. The following is an examplary configuration, if you do
not have any other databases set-up.

```yaml
databases:
  - nocodb
logins:
  - password: mysupersecretpassword
    username: nocodb_user
rights:
  - database: nocodb
    username: nocodb_user
```

**Note**: _Please change at least the 'password' of the MariaDB configuration._

### Add-on Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration running with MariaDB:

```yaml
database_name: nocodb
database_username: nocodb_user
database_password: mysupersecretpassword
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue.

```yaml
log_level: debug
```

Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`: Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

### Option: `reset_nocodb`

In case you want to reset NocoDB, you can set this flag. This will delete
all local files, including the SQLite. If you are running with MariaDB,
this flag will not delete those databases.

```yaml
reset_nocodb: true
```

**Note**: _After deleting the files, the option `reset_nocodb` will
automaticaly be removed from the add-on configuration._

## Authors & contributors

The original setup of this repository is by [Tobias Brenner][tobias].

## License

MIT License

Copyright (c) 2022 Tobias Brenner

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[tobias]: https://github.com/brenner-tobias
