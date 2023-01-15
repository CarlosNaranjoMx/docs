- [patron-de-inversion-de-control](#patron-de-inversion-de-control)
## patron-de-inversion-de-control

- [inyecion-de-dependencia-ejemplo](#inyecion-de-dependencia-ejemplo)
## inyecion-de-dependencia-ejemplo

```python
class Database:
    def __init__(self):
        self.connection = Connection()

class Connection:
    def __init__(self):
        self.status = "CONNECTED"

class BusinessLogic:
    def __init__(self, db: Database):
        self.db = db

# Create objects
db = Database()
bl = BusinessLogic(db)

# check the connection
print(bl.db.connection.status)
```
En este ejemplo, la clase BusinessLogic depende de la clase Database. En lugar
de crear una instancia de Database dentro de BusinessLogic, se inyecta una
instancia existente como argumento del constructor. Esto permite que
BusinessLogic sea independiente de cómo se crea Database y facilita la prueba de
BusinessLogic, ya que se puede proporcionar una instancia de prueba de Database
en lugar de una instancia real.