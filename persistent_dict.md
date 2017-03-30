```python
import json
class persistent_dict(dict):
    def __init__(self, filename):
        self.filename = filename
        try:
            with open(self.filename, 'r') as f:
                self.data = json.load(f)
                for key in self.data:
                    dict.__setitem__(self, key,self.data[key])
                
        except IOError:
            print "file not exist"
            
            
        
    def __setitem__(self,key,value):
        dict.__setitem__(self, key, value)
        self.write_file()

    
    def __delitem__(self,key):
        dict.__delitem__(self, key, value)
        self.write_file()

        
    def clear():
        dict.clear()
        self.write_file()
        
    def setdefault(self, key, value):
        dict.setdefault(self, key, value)
        self.write_file()
        
        
    def update(self, newdict):
        dict.update(self,newdict)
        self.write_file()
    
    
    def write_file(self):
        with open(self.filename, 'w') as f:
                    json.dump(self, f)
                    
                    
p = persistent_dict('data.json')
print p['db_name']
p['good'] = 'bad'
```