```python
import json

data = {
    'db_name' : 'ACME',
    'db_username' : '100',
    'db_password' : '542.23',
    'email_to' : '1',
    'data_query' : 'SELECT this, that FROM mytable WHERE col = 5' , 
    }
json_str = json.dumps(data)

with open('data.json', 'w') as f:
    json.dump(data, f)
    
print "write file"
```