# MySQLPython
Use MySQL in your project by object elements !

##Installation
First you have to modify the __init__ method by precising your ID.
At line 22:
```python
self.connection = pymysql.connect(host='**HOST**',
                                     user='**USER**',
                                     password='**PASSWORD**',
                                     db='**DB**',
                                     charset='utf8mb4',
                                     cursorclass=pymysql.cursors.DictCursor)
```
And then, in the file you have to deal with MySQL:
```python
import MySQLhandler.py
```
##Special rules about important column
Try to respect a convention:
  - Always get a field id
  - (Optional) A field created, which is auto-handle: it will add the datetime on the moment you create it
  - (Optional) A field modified, which is also auto-handle: it will write the datetime when you modify the entry

##Examples
###Get element
```python
clients = MySQL('customers_table')
clients.get('name', 'Steve Jobs')
```
It will print a dict with the row corresponding at your request, for example:
```python
{'name': 'Steve Jobs', 'job': 'CEO'}
```

### Add an element
For this you have to provide only useful field without id, created or modified field
You have to pass to the method an array with the field in the right order
Like this:
```python
clients = MySQL('customers_table')
clients.add(['Steve Jobs', 'CEO'])
```

###Modify an element
You have to give the method 3 parameters:
  -First the id you want to modify
  -Then the field you want to modify
  -Finally the new value
  
Like this:
```python
clients = MySQL('customers_table')
clients.modify(2, 'name', 'Stevie')
```

###Remove an element
Just provide the id to delete:
```python
clients = MySQL('customers_table')
clients.remove(2)
```
