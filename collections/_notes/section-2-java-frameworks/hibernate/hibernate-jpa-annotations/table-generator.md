---
layout: post
title: Annotation @TableGenerator
permalink: /:collection/hibernate/annotations/table-generator
---
 
annotation is used in a very similar way to the @SequenceGenerator annotation, but because @TableGeneratormanipulates a standard database table to obtain its primary key values, instead of using a vendor-specific sequence object, it is guaranteed to be portable between database platforms.

For optimal portability and optimal performance, you should not specify the use of a table generator, but instead use the @GeneratorValue(strategy=GeneratorType.AUTO) configuration, which allows the persistence provider to select the most appropriate strategy for the database in use.

optional attributes are as follows:
-	**allocationSize**: Allows the number of primary keys set aside at one time to be tuned for performance.
-	**catalog**: Allows the catalog that the table resides within to be specified.
-	**initialValue**: Allows the starting primary key value to be specified.
-	**pkColumnName**: Allows the primary key column of the table to be identified. The table can contain the details necessary for generating primary key values for multiple entities.
-	**pkColumnValue**: Allows the primary key for the row containing the primary key generation information to be identified.
-	**schema**: Allows the schema that the table resides within to be specified.
-	**table**: The name of the table containing the primary key values.
-	**uniqueConstraints**: Allows additional constraints to be applied to the table for schema generation.
-	**valueColumnName**: Allows the column containing the primary key generation information for the current entity to be identified.

