# Sales.py - Class

```python
import sqlite3

class Search:

    _conn = sqlite3.connect('sales.sqlite')
    
    def department_total(self, dept):
        """
        Returns the sum of all sales within a department
        """
        cursor = self._conn.execute("SELECT SUM(amount) FROM sales WHERE department = '" + dept + "'")
        return cursor.fetchone()[0]

    def department_total_bydate(self, dept, date):
        """
        Returns the sum of all sales within a department on a specific date
        """
        cursor = self._conn.execute("SELECT SUM(amount) FROM sales WHERE department = '" + dept + "' AND sale_date = '" + date + "'")
        return cursor.fetchone()[0]

    def country_count_date_range(self, country, start_date, end_date):
        """
        Returns the number of sales to buyers in a specific country between 2 dates, inclusive
        """
        cursor = self._conn.execute("SELECT SUM(amount) FROM sales JOIN buyers ON buyers.id = sales.buyer_id WHERE country = '" + country + "' AND sale_date >= '" + start_date + "' AND sale_date <= '" + end_date + "'")
        return cursor.fetchone()[0]

    def biggest_spender(self):
        """
        Returns a tuple with the first and last name of the buyer who spent the most money
        """
        cursor = self._conn.execute("SELECT first_name, last_name FROM buyers JOIN sales ON buyers.id = sales.buyer_id GROUP BY buyer_id ORDER BY SUM(amount) DESC LIMIT 1")
        return cursor.fetchone()

    def biggest_spenders(self, how_many, department):
        """
        Returns the how_many highest spenders in a specific department
        """
        cursor = self._conn.execute("SELECT first_name, last_name, SUM(amount) FROM buyers JOIN sales ON buyers.id = sales.buyer_id WHERE department = '" + department + "' GROUP BY buyer_id ORDER BY SUM(amount) DESC LIMIT " + str(how_many))
        return cursor.fetchall()
```

## SQLite Sales Search

### Department Total
The `department_total` method should return the total sales in `dept`.

### Department Total By Date
`department_total_by_date` returns the amount sold in a specific department `dept` on date `date`.

### Country Count Date Range
`country_count_date_range` should return the amount sold in a specific country between `start_date` and `end_date`, inclusive.

### Biggest Spender
`biggest_spender` returns a tuple with the first name and last name of whatever buyer has spent the most money.

### Biggest Spenders
`biggest_spenders` returns a list of the top `how_many` spenders in `department`. 

Each element of the list should be a tuple with the first name, last name, and amount; in that order. 

Note on this one. I should return up to `how_many` of the highest spenders. It's possible that there may not be `how_many` spenders in a specific department. It's also possible that there aren't any in which case this method should return an empty list. 
