# Python SQL return code


Simple test file

```python
from unittest import result
from datastore import Datastore

db = Datastore()

result = db.get_fees(3)

try:
    print(*result, sep="\n")
except BaseException:
    print(result)


print(f"{len(result)} record processed")
```

This spits out a list of whatver your returning on your code


An example of a return statement on the db method file
```python
results = self.cur.fetchall()
        
if results == None:
    return None
else:
    return results
```
