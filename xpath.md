# xpath

```
<?xml version="1.0"?>
<employeeInfo>
  <employee id="123">
    <name almaMater="Downing College">John Cleese</name>
    <sketch>The Ministry of Silly Walks</sketch>
  </employee>
  <employee id="456">
    <name>Eric Idle</name>
    <sketch>  Nudge Nudge  </sketch>
  </employee>
  <employee id="789">
    <name almaMater="University of Oxford">Michael Palin</name>
    <sketch>The Fish Slapping Dance</sketch>
    <books>
      <book>Around the World in 80 Days</book>
      <book>Brazil</book>
    </books>
  </employee>
</employeeInfo>


Name element with text = John Cleese
//name[.='John Cleese']
//name[text()='John Cleese']

... or contains eese
//name[contains(., 'eese')]
//name[contains(text(), 'eese')]

Name element with attribute = Downing College
//name[@almaMater='Downing College']


All child employee elements of employeeInfo
/employeeInfo/employee

All employee elements in entire doc
//employee

All employee descendants of employeeInfo
/employeeInfo//employee

Number of employee elements in entire doc
count(//employee)

Employees with id = 456
//employee[@id=456]

Second employee name text
//employee[2]/name/text()

Third employee almaMater attribute
//employee[3]/name/@almaMater

Employees whose name is John Cleese
//employee[name='John Cleese']

Employees whose name starts with John
//employee[starts-with(name, 'John')]

Names that start with John
//employee/name[starts-with(., 'John')]/text()

Employees who went to Oxford
//employee[name[@almaMater='University of Oxford']]

Name of employees who went to Oxford
//employee/name[@almaMater='University of Oxford']/text()

John Cleese's alma mater:
//name[.='John Cleese']/@almaMater
//name[text()='John Cleese']/@almaMater

Employees whose sketch when normalized is Nudge Nudge and name contains Idle
//employee[normalize-space(sketch)='Nudge Nudge'][contains(name, 'Idle')]
//employee[normalize-space(sketch)='Nudge Nudge' and contains(name, 'Idle')]

Employees whose sketch is The Fish Slapping Dance or The Ministry of Silly Walks
//employee[sketch='The Fish Slapping Dance' or sketch='The Ministry of Silly Walks']

Employees with alma mater populated
//employee[name[@almaMater]]

Employees who wrote the book Brazil
//employee[books[book[text()='Brazil']]]

Last employee
//employee[last()]

All employee child elements
//employee/*

All employee elements and name elements
//employee|//name
```
