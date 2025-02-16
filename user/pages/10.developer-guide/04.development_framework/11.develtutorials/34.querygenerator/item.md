---
title: 'Query Generator'
metadata:
    description: 'Query Generator'
    author: 'Joe Bordes'
content:
    items:
        - '@self.children'
    limit: 5
    order:
        by: date
        dir: desc
    pagination: true
    url_taxonomy_filters: true
taxonomy:
    category:
        - development 
        - querygenerator
    tag:
        - howto
---

Query Generator is a class that will easily generate complex SQL queries for us. It will permit us to define some high-level fields and conditions and return all the necessary joins and conditions to get the information we need.

===

Besides giving us all the joins we need to get the information we are looking for it will also optimize the query to be as low cost as possible.

The best place to start is [in the unit tests](https://github.com/tsolucio/coreBOSTests/blob/master/include/QueryGenerator/QueryGeneratorTest.php).
The [Query Generator unit tests](https://github.com/tsolucio/coreBOSTests/blob/master/include/QueryGenerator/QueryGeneratorTest.php)
show a full set of the different ways this powerful class can be used.

### coreBOS List Filters

The filter syntax is a rather complex structure that was created before we had Query Generator so it is used throughout the application. When QG was created it was given a set of methods to directly convert the filter syntax into the QG syntax. Two of those functions are useful as a "different" way to load conditions into a Query Generator object.

**constructAdvancedSearchConditions** will return the coreBOS List Filter syntax from an array of fields and conditions. The structure returned from this method can be directly fed into the method **addUserSearchConditions** to set the query conditions.

Here are two examples and you can see a few more [in the unit tests](https://github.com/tsolucio/coreBOSTests/blob/master/include/QueryGenerator/QueryGeneratorTest.php#L1331).

```php
$queryGenerator = new QueryGenerator('Accounts', $current_user);
$conds = array(
	array(
		array(
			'field' => 'accountname',
			'op' => 'c',
			'value' => 'al',
			'glue' => '',
		),
	),
);
$filter = $queryGenerator->constructAdvancedSearchConditions('Accounts', $conds);
$queryGenerator->addUserSearchConditions($filter);
// user querygenerator normally, the conditions are set
// where accountname like '%al%'
```

```php
$queryGenerator = new QueryGenerator('Accounts', $current_user);
$conds = array(
	array(
		array(
			'field' => 'accountname',
			'op' => 'c',
			'value' => 'al',
			'glue' => 'and',
		),
		array(
			'field' => 'employees',
			'op' => 'g',
			'value' => '15',
			'glue' => '',
		),
	),
);
$filter = $queryGenerator->constructAdvancedSearchConditions('Accounts', $conds);
$queryGenerator->addUserSearchConditions($filter);
// user querygenerator normally, the conditions are set
// where accountname like '%al%' and employees > 15
```