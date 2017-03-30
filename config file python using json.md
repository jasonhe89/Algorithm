```python
import json
import os 
class Config:
    def __init__(self, filename, overwrite_keys):
        self.filename = filename
        self.overwrite_keys = overwrite_keys
        try:
            with open(self.filename, 'r') as f:
                self.data = json.load(f)
        except IOError:
            print "file not exist"
            
    def get(self,key):
        try:
            return self.data[key]
        except KeyError:
            print "key not exist in the file"
    
    def set(self, key, value):
        if key in self.data:
            if self.overwrite_keys is True:
                self.data[key] = value
                try:
                    with open(self.filename, 'w') as f:
                        json.dump(self.data, f)
                except IOError:
                    print "write to file failed"
            else:
                print "key already in the file, current mode not support overwrite"
                raise ValueError
        else:
            self.data[key] = value
            try:
                with open(self.filename, 'w') as f:
                    json.dump(self.data, f)
            except IOError:
                print "write to file failed"
        
                

conf = Config('data.json', overwrite_keys=True)
print conf.get('1')   # dbuser
query = conf.get('data_query')  # SELECT this, that FROM 
print query
conf.set('confkey1', 'newval')
```