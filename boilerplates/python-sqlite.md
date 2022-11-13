# Datastore

## **datastore.py**
```python
import sqlite3

class Datastore:
    
    def __init__(self, db_file_name: str):
        """
        initialize  Datastore Object
        """

        self.connection = sqlite3.connect(db_file_name)
        self.cursor = self.connection.cursor()


    def __del__(self):
        """
        Writes data from chache to drive and then closes connection
        """
        self.connection.close()
```

##  **test.py**
```python
from datastore import Datastore

db = Datastore("netflix.db")
```