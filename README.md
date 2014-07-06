# SchemaManager
Manage database schema based on schema definition file.

## Usage
Creates Diff with 2 schema files and logs out their diff.

```ruby
puts SchemaManager::Diff.new(
  before: File.read("before.sql"),
  after: File.read("after.sql"),
  type: "mysql"
)
```

The result would be the following:

```sql
BEGIN;

SET foreign_key_checks=0;

CREATE TABLE `items` (
  `id` integer(10) unsigned NOT NULL auto_increment,
  `user_id` integer(10) unsigned NOT NULL,
  `name` varchar(255) NULL DEFAULT NULL,
  INDEX `user_id` (`user_id`),
  PRIMARY KEY (`id`)
);

SET foreign_key_checks=1;

COMMIT;
```

## Note
So far, we are aimed at supporting MySQL for the 1st prototype.

### TODO
There are a lot of things to do. We welcome your contributions!

* Geenrate SchemaManager::Diff from 2 SchemaManager::Schema
* Generate SQL representation from SchemaManager::Diff
