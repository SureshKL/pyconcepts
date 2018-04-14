
# Parse the XML from string data


```python
data = '''<?xml version="1.0"?>
<data>
    <country name="Liechtenstein">
        <rank>1</rank>
        <year>2008</year>
        <gdppc>141100</gdppc>
        <neighbor name="Austria" direction="E"/>
        <neighbor name="Switzerland" direction="W"/>
    </country>
    
    <country name="Singapore">
        <rank>4</rank>
        <year>2011</year>
        <gdppc>59900</gdppc>
        <neighbor name="Malaysia" direction="N"/>
    </country>
    
    <country name="Panama">
        <rank>68</rank>
        <year>2011</year>
        <gdppc>13600</gdppc>
        <neighbor name="Costa Rica" direction="W"/>
        <neighbor name="Colombia" direction="E"/>
    </country>
</data>'''
```

### Import the ElementTree class with standard alias "ET"


```python
import xml.etree.ElementTree as ET
```

### Parsing XML from string data gives the root node 


```python
root = ET.fromstring(data)
print(root.tag)
```

    data


### Get all direct children of root element


```python
for child in root:
    print(child.tag, child.attrib)
```

    country {'name': 'Liechtenstein'}
    country {'name': 'Singapore'}
    country {'name': 'Panama'}


### Get "year" from first node "country"


```python
print(root[0][1].text)
```

    2008

