# Materialized View

A Materialized View is a database object that contains the results of a query. It is a physical copy, snapshot or a representation of the base table(s) that are stored on the disk like a regular table with a set of precomputed rows. 

The query can be a join or aggregated data, such as the sum of sales. Materialized views are used as a performance-enhancing technique. When you create a materialized view, Oracle Database creates one internal table and at least one index, and may create one view, all in the schema of the materialized view.

Materialized views can be refreshed periodically using the original base tables to get updated data, thereby making the Materialized View synchronous with the base tables. 

Here's an example of creating a materialized view in SQL:

```sql
CREATE MATERIALIZED VIEW sales_summary AS
SELECT product_id, SUM(sales) as total_sales
FROM sales
GROUP BY product_id;
```

In this example, `sales_summary` is a materialized view that stores the total sales for each product. The database would keep this data stored so that it can quickly return the total sales for a product without needing to perform the aggregation every time.

Materialized views are particularly useful when you have heavy aggregations or complex joins that are performed frequently, as they can speed up query performance by pre-calculating the expensive parts of the query. However, they do take up additional storage space, and there is a cost associated with keeping them up-to-date.
