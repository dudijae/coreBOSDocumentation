---
title: 'Import Business Mapping'
metadata:
    description: 'This map permits you to mass import large files from the command line.'
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
        - adminmanuals
        - businessmappings
    tag:
        - import
---

The CoreBOS Import Business Mapping is a tool designed for developers and implementers, enabling them to perform mass imports of large files from the command line. It supports two different import methods

===

coreBOS based import process
----------------------------

This method will use the same import process that is used from the application itself, the only difference is that through this map you can launch the whole process from the command line, making it easy to do unattended batch imports without having to go through the UI steps every time. All the other application import features are identical.

<div class="notices red">
The import CSV file MUST have a header and be in UTF8 format
</div>

The accepted format is

```xml
<map>
  <mapname>application map name, saved while doing test import</mapname>
  <delimiter>,|;</delimiter>
  <duplicates>
  <handling>skip|overwrite|merge</handling>
  <fields>
    <name>fieldname</name>
    ...
  </fields>
  </duplicates>
</map>
```

The map name is mandatory. The idea is that you will launch a test
import with a few rows and define the map with the field mapping and
then use the name of that map in the business map so that the import
process knows what to do. Remember to set default values, if needed.

If no delimiter is given, the comma will be used.

The duplicates section may be empty/missing in which no duplicates control will be applied.

This is an example of a real import business map:

```xml
<map>
  <mapname>cbimportBM1</mapname>
</map>
```

Direct save import process
--------------------------

This is a custom import process implemented in the business map itself.

It has a different way of handling duplicates, permitting to update all duplicate records it finds or only the first/last one. It updates/creates records with a direct coreBOS save which does not launch workflows and will be faster than the normal coreBOS import process (which does launch them and the save process is a bit more complex).

To import relations you must indicate the field to search on in the related module in the map.

The accepted format is

```xml
<map>
  <targetmodule>
    <targetname>ProductDetail</targetname>
  </targetmodule>
  *
  <fields>
    <field>
      <fieldname>productvin</fieldname>
      <fieldID></fieldID>
      <value>productvin</value>
      <predefined></predefined>
      <Orgfields>
        <Relfield>
          <RelfieldName>cf_880</RelfieldName>
          <RelModule>Products</RelModule>
          <linkfield>productvin</linkfield>
        </Relfield>
      </Orgfields>
    </field>
    ...
  </fields>
  <matches>
    <match>
      <fieldname>productdetailname</fieldname>
      <fieldID> </fieldID>
      <value>productdetailname</value>
      <predefined></predefined>
    </match>
    ...
  </matches>
  <options>
    <update>FIRST/LAST/ALL</update>
  </options>
</map>
```

Execute import process
----------------------

To execute the import you have to launch this command from the root of your coreBOS install

```php
php modules/cbMap/processmap/importCSV.php file_to_import.csv name_or_id_of_business_map [thread]
```

The **thread** optional parameter is an alphanumeric string that will be concatenated to the import database temporary table. This permits us to launch various imports in parallel as long as different thread identifier strings are used.

<div class="notices blue">
Since the business map for both supported methods is different, depending on the type of map found the correct process will be launched.
</div>

<br>
------------------------------------------------------------------------

[Next](../08.duplicaterecords) | Chapter 17: Duplicate Records.

------------------------------------------------------------------------