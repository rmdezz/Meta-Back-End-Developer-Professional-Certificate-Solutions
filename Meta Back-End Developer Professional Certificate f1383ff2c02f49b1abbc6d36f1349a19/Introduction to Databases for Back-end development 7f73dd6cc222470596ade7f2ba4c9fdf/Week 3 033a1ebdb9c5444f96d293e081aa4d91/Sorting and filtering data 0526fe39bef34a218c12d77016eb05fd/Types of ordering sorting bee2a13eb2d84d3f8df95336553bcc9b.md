# Types of ordering/sorting

Let’s review some example scenarios that use the ORDER BY clause using the tables in the sample database. You can give SQL SELECT statements using the ORDER BY clause with ASC and DESC keywords as required for these scenarios.

# Examples of the ORDER BY clause

## Sorting by a single column:

To sort the data in the customer table by descending order of the Customer ID field, you would use the following query:

```sql
SELECT * 
FROM customers 
ORDER BY CustomerId DESC;
```

## Ordering by multiple columns:

To sort invoice data by both billing city and invoice date in ascending order of BillingCity and descending order of InvoiceDate, you would use the following query:

```sql
SELECT * 
FROM invoices 
ORDER BY BillingCity ASC, InvoiceDate DESC;
```

# Conclusion

The ORDER BY clause is a powerful tool for sorting data in a MySQL database. By mastering its syntax and usage, you can easily sort data in a variety of ways and make it more organized and readable. With the knowledge and examples provided in this task, you will be able to use the ORDER BY clause in various practical scenarios and make effective use of the ASC and DESC keywords for ordering data.