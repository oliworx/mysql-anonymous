# Mysql Anonymous

Developers can benefit from having real data when they are
developing. 
This script can do a few things (see `anonymize.yml`):

### Operations

* **truncate**: Deletes all rows in the table
* **nullify**: Sets the value to NULL (None), or blank string if null isn't allowed
* **random_int**
* **random_ip**
* **random_email**: Sets the value to `<id>@example.com`
* **field_id**: Sets the value to `<field>/<id>` e.g. `feedback_text/4`
* **random_date**: Generates random date between 1970 and now
* **random_phonenumber**: Generates a random phone number with an Edinburgh area code
* **hash_value**: Sets the value to an MD5 hashed version of the original value `3a66dc10`
* **hash_email**: Sets the value to an MD5 hashed version of the original value as an email i.e. `7815696e@example.com`
* **empty_string**: Sets the value to an empty string
* **fixed_string**: Sets the value to an fixed string

### Features

* Truncate any tables (logs, and other cruft which may have sensitive data)
* Nullify fields (emails, passwords, etc)
* Fill in random/arbitrary data:
    * Random integers
    * Random IP addresses
    * Email addresses
    * Usernames
* Delete rows based on simple rules:  e.g.
  ``DELETE FROM mytable WHERE private = "Yes"``:

```
    database:
        tables:
            mytable:
                delete:
                    private: Yes
```

### Usage

    python anonymize.py > anon.sql
    cat anon.sql | mysql
