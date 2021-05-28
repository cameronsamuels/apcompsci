# import_json.py - Method

```python
import sqlite3
import json

_conn = sqlite3.connect('data.sqlite')

def data_type(self, val):
        val_type = ''
        if str(val).isdigit() and len(str(val)) <= 6:
            val_type = 'INTEGER'
        elif '.' in str(val) and str(val).replace('.', '', 1).isdigit():
            val_type = 'DECIMAL'
        elif len(str(val)) == 19 and val[0:4].isnumeric() and val[4] == '-' and val[5:7].isnumeric() and val[7] == '-' and val[8:10].isnumeric() and val[10] == ' ' and val[11:13].isnumeric() and val[13] == ':' and val[14:16].isnumeric() and val[16] == ':' and val[17].isnumeric():
            val_type = 'DATETIME'
        else:
            val_type = 'TEXT'
        return val_type
        
def import_json(self, filename):
        with open(filename) as json_file:
            data = json.load(json_file)
            table = filename.replace('.json', '')
            fields = ''
            sql = 'CREATE TABLE ' + table + ' (id INTEGER PRIMARY KEY,'
            for x in data[0].keys():
                fields += x + ','
                sql += x + ' ' + self.data_type(data[0][x]) + ','
            fields = fields[0:-1]
            self._conn.execute(sql[0:-1] + ')')
            for row in data:
                sql = 'INSERT INTO ' + table + ' (' + fields + ') VALUES ('
                for f in fields.split(','):
                    typ = self.data_type(row[f])
                    if typ == 'INTEGER' or 'DECIMAL' in typ:
                        sql += str(row[f]) + ','
                    else:
                        sql += '"' + row[f] + '",'
                self._conn.execute(sql[0:-1] + ')')
                self._conn.commit()
```

## The method
`import_json` reads `filename` and imports into `data.sqlite` in a table named the same as the file, minus the extension. For example, `cars.json` should import into a table called `cars`.
