# WordPress to Opencart Customers passwords migartion
This is a minor change to the OpenCart code, which facilitates the migration of customers from WordPress to OpenCart.

What this change do?

This code is integration of the WordPress password checker inside OpenCart. It can help developers, who want to migrate users from WordPress to Opencart.

The code is working very simple - when some user try to login in the new site based on OpenCart, the code compares entered password with the old hash, exported from WordPress. If the entered password match with the hash, code just fill the "password" and "salt" columns in the database in the standard SHA-1 format, used by OpenCart.

The code works only if user try to login for a first time.

How to use it:

1. Create a new SQL query in your OpenCart database.

ALTER TABLE `customer` ADD `old_password` VARCHAR(40) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL AFTER `fax`;

2. Migrate your WordPress customers to your OpenCart database and put the old passwords from "users" table ("user_pass" column) to "old_password" column in the OpenCart database.

3. Put "class-phpass.php" file inside "/system/helper/" folder in your OpenCart project.
4. Replace your "customer.php" file inside "/system/library/" folder with the new one.
