## Search.py - Class

```python
import xml.etree.ElementTree as ET 
import dateutil.parser

class Search:
    
    def round_dictionary(self, dict, decimals=2):
        """
        Rounds all values to no more than 2 decimal places. You'll
        need to call this on your dictionaries before returning to
        take care of any floating point weirdness.

        Note: You'll only need this in the methods that return
        dictionaries with a floating point value. 
        """
        for key in dict:
            dict[key] = round(dict[key], 2)
        return dict 

    def amount_spent(self, category):
        """
        Returns the amount spent in category
        """
        tree = ET.parse('sales-data.xml')
        root = tree.getroot()
            
        total = 0

        for sale in root.findall('./person'):
            if category == sale.find('category').text:
                total += float(sale.find('amount').text)

        return total
            
    def spent_by_gender(self):
        """
        Returns a dictionary with a M and F key and the
        amount spent by each gender
        """
        tree = ET.parse('sales-data.xml')
        root = tree.getroot()
        
        total = {
            "F": 0,
            "M": 0
        }

        for sale in root.findall('./person'):
            gender = sale.find('gender').text
            amount = float(sale.find('amount').text)
            total[gender] += amount

        return self.round_dictionary(total)
        
    def all_categories(self):
        """
        Returns a dictionary with amounts spent in each
        category. The category should be the key, the
        sum of all sales in that category is the value
        """
        tree = ET.parse('sales-data.xml')
        root = tree.getroot()

        total = {}

        for sale in root.findall('./person'):
            cat = sale.find('category').text
            amount = float(sale.find('amount').text)
            if not cat in total:
                total[cat] = amount
            else:
                total[cat] += amount

        return self.round_dictionary(total)

    def spent_between(self, start_date, end_date):
        """
        Returns the sum of all sales between start_date
        and end_date, inclusive
        """
        tree = ET.parse('sales-data.xml')
        root = tree.getroot()

        total = 0

        for sale in root.findall('./person'):
            timestamp = dateutil.parser.parse(sale.find('timestamp').text)
            if timestamp >= start_date and timestamp <= end_date:
                total += float(sale.find('amount').text)

        return total
```

## Amount Spent
The first method, `amount_spent`, should go through the data file and find the amount spent in a specified category. For example, `amount_spent('Baby')` would return the amount spent in the `Baby` category.

## Spent by Gender
`spent_by_gender` returns a dictionary with the amount spent for each gender. Keys should be `"M"` and `"F"`.  Key order does not matter. 

Be sure to run your dictionary through `round_dictionary` before returning. 

## All Categories
`all_categories` returns a dictionary of the amount spent in each category, with the category name as key and amount as value. 

Category names are case sensitive, although it doesn't matter because they don't vary in the data. You won't see both `computers` and `Computers`. Category names are all title cased.

The order of keys does not matter. The auto grader will consider `{"A": 12, "B": 16}` and `{"B": 16, "A": 12}` equal. 

## Spent Between
The `spent_between` method takes a `start_date` and `end_date` and returns the amount of sales between those two dates, inclusive.

`start_date` and `end_date` are both timestamps, not strings. You'll need to convert the `timestamp` field from the XML from a string to a timestamp to be able to compare. To do that use the `dateutil.parser.parse(date_string)` method. It will convert the string representation `date_string` to a timestamp. Once that's done you can compare the dates just like numbers with `<`, `>`, `<=` and `>=`.
