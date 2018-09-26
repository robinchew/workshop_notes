Format String
-------------

```
first_name = 'James'
last_name = 'Bond'
age = 55
```
```
'The name is '+last_name + '. '+first_name + ' ' + last_name + '. And I am ' + str(age)
'The name is {}. {} {}. And I am {}'.format(last_name, first_name, last_name, age)
'The name is {1}. {0} {1}. And I am {2}'.format(first_name, last_name, age)
'The name is {last_name}. {first_name} {last_name}. And I am {age}'.format(first_name=first_name, last_name=last_name, age=age)
'The name is {last_name1}. {first_name1} {last_name1}. And I am {age1}'.format(first_name1=first_name, last_name1=last_name, age1=age)
```
All results in:
```
'The name is Bond. James Bond. And I am 55'
```

Write Multiline String & Save in a File
---------------------------------------

```
f = open('table.html', 'w')
var = 124

body = '''
    <h1>Heading.</h1>
    <p>Paragraph {}.</p>
'''.format(var)

line = 'Heading. Paragraph {}.'.format(var)

f.write(line + body)
f.close()
```
