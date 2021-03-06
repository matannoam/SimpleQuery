# SimpleQuery
query from containers of objects, in Python

## Query pattern

The Query pattern uses criteria on classes and fields to retrieve
value objects from a dataset. Those criteria are a field, an operator,
and a value. For example, ('last_name', =, 'Fowler') or ('price', <, 100.00).

## Installation

```
pip install simple-query
```

## Usage
`all() ` returns the matching objects for a query, and `filter(*criteria)` returns a new, filtered query, where `criteria = field, operator, value`.

For example:
```Python
from simple_query.query import Query
from operator import eq, gt, lt

people = [
    Person('Ada Lovelace'),
    Person('Grace Hopper'),
    Person('Jean Bartik')]

Query(people).all()
# [Person('Ada Lovelace'), Person('Grace Hopper'), Person('Jean Bartik')]

Query(people).filter('last_name', eq, 'Lovelace').all()
# [Person('Ada Lovelace')]

Query(people) \
    .filter('first_name', gt, 'B') \
    .filter('last_name', lt, 'C').all()
# [Person('Jean Bartik')]
```

## Setting up development environment
It is always recommended to use a virtual environment for each
Python appplication. Create the environment once, after cloning
this repository to your machine.
```
python3 -m venv .env
```

For each terminal session going forward, work on the virtual
environment and use its copy of python.
```
source .env/bin/activate
```

Upgrade pip
```
pip install -U pip
```

Install developer requirements for a nicer test runner (see Running Tests)
```
pip install -r requirements/dev.txt
```

## Running tests
Tests are written in unittest syntax, so no additional package are needed
to run them
```
python -m unittest discover
```
For a more informative output, as well as plugins for
color and watch mode, use nose test runner. You can also use the test runner
of your choice.
```
nosetests --rednose --with-watch
```
