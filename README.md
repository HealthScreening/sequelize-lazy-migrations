# sequelize-lazy-migrations

> ⚠️ Repository Archived ⚠️ [2022-08-16]
>
> According to [the DOE](https://www.schools.nyc.gov/school-life/health-and-wellness/covid-information/health-and-safety-in-our-schools#jump-to-heading-0), for the 2022-2023 school year, the health screening will not be required.
> * Daily Health Screener:
>   * No longer required to enter school buildings 
>
> This means that this repository will be archived.

Migration generator & runner for sequelize

This package provide two tools:
* `makemigration` - tool for create new migrations
* `runmigration` - tool for apply created by first tool migrations

## Install
`npm install @healthscreening/sequelize-lazy-migrations`

## Usage
* Init sequelize, with sequelize-cli, using `sequelize init`
* Create your models
* Create initial migration - run:

`makemigration --name <migration name>`
* Change models and run it again, model difference will be saved to the next migration

To preview new migration, without any changes, you can run:

`makemigration --preview`

`makemigration` tool creates `_current.json` file in `migrations` dir, that is used to calculate difference to the next migration. Do not remove it!

To create and then execute migration, use:
`makemigration --name <name> -x`

## Executing migrations
* There is simple command to perform all created migrations (from selected revision):

`runmigration`
* To select a revision, use `--rev <x>`
* If migration fails, you can continue, use `--pos <x>`
* To prevent execution next migrations, use `--one`


For more information, use `makemigration --help`, `runmigration --help`

## TODO:

* Unit tests
* Migration action sorting procedure need some fixes. When many foreign keys in tables, there is a bug with action order. Now, please check it manually (`--preview` option)
* Need to check (and maybe fix) field types: `BLOB`, `RANGE`, `ARRAY`, `GEOMETRY`, `GEOGRAPHY`
* Downgrade is not supported, add it
* This module tested with postgresql (I use it with my projects). Test with mysql and sqlite.
