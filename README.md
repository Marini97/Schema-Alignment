# Assignment on “Big Data Integration”
## Schema Alignment

Implementation of the proposed approach on the dataset of the [DI2KG challenge](http://di2kg.inf.uniroma3.it/2020/#challenge). 

The Schema matching task consists in identifying mappings between source attributes (e.g. the attribute "brand" from source "www.ebay.com") and a set of target attributes (e.g. "brand", "dimensions", "screen_size", etc.) defined in a given mediated schema.

Participants to the Schema matching task are provided with the mediated schema (in TXT format, one target attribute per row) and a labelled dataset in CSV format (i.e., $Y^{SM}_v$), containing two columns: "source_attribute_id" and "target_attribute_name":

- the "source_attribute_id" is a global identifier for an attribute at source level. For instance, the source_attribute_id "www.ebay.com//screen size" refers to all the "screen size" attributes from specs in source "www.ebay.com". All "source_attribute_id" in the labelled dataset $Y^{SM}_v$ refer to one or multiple target attributes (or properties) of the given mediated schema. Thus, the dataset $Y^{SM}_v$ provides a subset of mappings from source attributes in the specs dataset $X_v$ and target attributes in the mediated schema;
- the "target_attribute_name" is the name of the target attribute in the mediated schema (e.g. "brand", "screen_size", etc.).

Example of $Y^{SM}_v$
```
    source_attribute_id, target_attribute_name
    www.ebay.com//producer name, brand
    www.ebay.com//brand, brand
    www.odsi.co.uk//device type, screen_type
    www.odsi.co.uk//device type, screen_size_diagonal
```
Note that some source attribute have values refer to multiple target attributes. Therefore, there might be source attributes with mappings to more than one target attribute. For instance, if the set of values related to the source attribute "www.odsi.co.uk//device type" is the following:

- value1: "LED-backlit LCD monitor - 23''"
- value2: "23''"
- value3: "LED LCD"

Then this source attribute is mapped with target attributes "screen_type" (because of value1 and value3) and "screen_size_diagonal" (because of value1 and value2).

The goal is to find mappings between source attributes in the dataset $X_v$ and target attributes of the mediated schema. The output is stored in a CSV file containing all the mappings found by the system. The CSV file has two columns: "source_attribute_id" and "target_attribute_name", separated by comma.