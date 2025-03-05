```python
thisdict = {  
  "brand": "Ford",  
  "model": "Mustang",  
  "year": 1964  
}
```

Dictionaries are used to store data values in key:value pairs.
A dictionary is a collection which is ordered*, changeable and ==do not allow duplicates.==

> As of Python version 3.7, dictionaries are _ordered_. In Python 3.6 and earlier, dictionaries are _unordered_.

```python
thisdict = {  
  "brand": "Ford",  
  "model": "Mustang",  
  "year": 1964  
}  
print(thisdict)

# {'brand': 'Ford', 'model': 'Mustang', 'year': 1964}
```


##### Dictionary Items

- Dictionary items are ordered, changeable, and do not allow duplicates.
- Dictionary items are presented in key:value pairs, and can be referred to by using the key name.

```python
thisdict = {  
  "brand": "Ford",  
  "model": "Mustang",  
  "year": 1964  
}  
print(thisdict["brand"])

# Ford
```

##### The dict() Constructor
```python
thisdict = dict(name = "John", age = 36, country = "Norway")  
print(thisdict)
```

#####  Accessing Items

```python
thisdict = {
	"brand": "Ford",
	"model": "Mustang",
	"year": 1964
}

x = thisdict["model"]
```

