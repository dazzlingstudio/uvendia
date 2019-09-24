# Accessing the data
After you have inserted your assets into **Uvendia** asset management system, it's time to access them on the front-end.

## Uvendia Data Access Context
**Uvendia** has a ``public static class UvendiaContext`` from where you can access all the data you need. You can use this ``UvendiaContext`` for accessing and persisting data into the database.
Example code:

```C#
var categories = UvendiaContext.Categories.GetByStoreId(settings.StoreId);
```
> You can store the ``StoreId`` on the **Umbraco** ``HomePage``, under a ``document type`` section ``App Settings`` containing a ``number`` text input.

Or for selecting featured products (see [plug-ins](#umbraco-plug-ins) paragraph):
```C#
var featuredProducts = UvendiaContext.Products.All(featuredProductIds.Split(',').Select(f => long.Parse(f)).ToArray());
```

### Dapper
**Uvendia** ``Data Access Layer`` is using [Dapper](https://github.com/StackExchange/Dapper) as ORM (Object Relational Mapper). In terms of speed is it as ``fast`` as using a raw ADO.NET data reader. But it comes with one tradeoff, you need to write some ``old-fashioned`` queries. But the mapping to ``bussiness objects`` is being done for you by ``Dapper``.

### SQL Injections
> Dapper is very secure if you used it as described in their tutorials. Make sure that your ``parameters`` are passed as SQL command parameters.

Passing parameters:

```C#
public override Product Single(int id)
{
    var sql = "select * from Product p where p.Id = @Id;";

    using (var conn = CreateConnection())
    {
        var lookup = conn.Query(sql, new { Id = id });
        var pay = lookup.FirstOrDefault();
        return pay;
    }
}
```
### Source code documentation
For accessing complex assets like ``Product``, ``Category``, ``Event``, ``Store`` and ``Order``, it is very important you take a look at our [Source code documentation](#).

## Querying the database
When querying all assets using conditions (like the ``where`` clause), take a look first at your Visual Studio documentation intellisense when accessing the ``All`` method. The documentation is also available [here](#)

```C#
UvendiaContext.Stores.All(string where = null, string orderBy = null, int top = 0, object parms = null)
```

Each joined table has an ``Alias``.
Using the ``All`` method code example:
```C#
UvendiaContext.Stores.All("s.Published=@published", parms: new { published = true})
```

> Make sure you use the ``parms`` parameter to pass the values of your conditions to avoid ``SQL Injections``.

> For a more extended demo of how you can use the ``UvendiaContext``, please download our [demo project](/webshop/demowebshop.md).

## Search
For searching ``Products`` or ``Events`` you can use our ``Database Catalog`` where all the searchable fields are indexed. 
```C#
UvendiaContext.Products.Search();
```
Or
```C#
UvendiaContext.Events.Search();
```

> In case you have a very big webshop with more than 10K items, we recommend you to use a more suitable data indexer like [Elastic Search](https://www.elastic.co/) or [Solr](https://lucene.apache.org/solr/).

## Umbraco plug-ins
**Uvendia** has two plug-ins you can use for selecting products on your **Umbraco** content pages:

* ``Uvendia ProductTreePicker``
    - If you have a small set of products (±5000), you can use this tree node for selecting products assigned to categories.
* ``Uvendia ProductSelector``
    - Use this ``autocomplete`` ``multi-selector`` in case you have a lot of products (>10.000+). Start by filling in the product ``SKU`` OR ``Name`` and the products meeting that criteria will show up.
 