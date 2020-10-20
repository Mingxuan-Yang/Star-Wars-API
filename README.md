# Data Extraction Using Star Wars API

*Project Date: 2020-10-17*

## Introduction

This project is to extract data through SWAPI, the Star Wars API, in the Python environment. The details of SWAPI can be obtained at its [documentation](https://swapi.dev/documentation). SWAPI provides six attributes about Star Wars. They are

- `films`
- `people`
- `planets`
- `species`
- `starships`
- `vehicles`

These data can be rendered by two types of encodings in SWAPI, which are

- JSON (default)
- Wookiee

In this project, JSON is the format used to extract the data. After getting the data, two problems need to be solved:

- The name of the oldest person (or robot or alien)
- The titles of all the films the oldest creature appeared in

## Data Extraction

`requests` library is applied to extract data. The information about people i can be obtained through the following code.

```python
import requests

people_i = requests.get('https://swapi.dev/api/people/i').json()
```

The result for person 1 is:

```python
{'name': 'Luke Skywalker',
 'height': '172',
 'mass': '77',
 'hair_color': 'blond',
 'skin_color': 'fair',
 'eye_color': 'blue',
 'birth_year': '19BBY',
 'gender': 'male',
 'homeworld': 'http://swapi.dev/api/planets/1/',
 'films': ['http://swapi.dev/api/films/1/',
  'http://swapi.dev/api/films/2/',
  'http://swapi.dev/api/films/3/',
  'http://swapi.dev/api/films/6/'],
 'species': [],
 'vehicles': ['http://swapi.dev/api/vehicles/14/',
  'http://swapi.dev/api/vehicles/30/'],
 'starships': ['http://swapi.dev/api/starships/12/',
  'http://swapi.dev/api/starships/22/'],
 'created': '2014-12-09T13:50:51.644000Z',
 'edited': '2014-12-20T21:17:56.891000Z',
 'url': 'http://swapi.dev/api/people/1/'}
```

One thing that worths some attention is that certain websites might not be found, which is known as the 404 Error. In this case, storing their information will be a waste of time and space. The `requests` package offers some methods to check this issue. The example to check the validity of website `https://examples` is shown as

```python
requests.get('https://examples').status_code
```

If the value returned is 404, it indicates that the 404 Error exists for this website. Conversely, if 200 is returned, it means that this website is able to be fetched.

## Results

**The name of the oldest person (or robot or alien)**

Based on `people` attribute of SWAPI, the oldest creature is Yoda, which is born in 896BBY, where BBY indicates before the Battle of Yavin.

**The titles of all the films the oldest creature appeared in**

Based on `people` and `films` attributes of SWAPI, the titles and other information of the films that Yoda appeared in are

|title|release_date|
|:---:|:---:|
|The Empire Strikes Back|1980-05-17|
|Return of the Jedi|1983-05-25|
|The Phantom Menace|1999-05-19|
|Attack of the Clones|2002-05-16|
|Revenge of the Sith|2005-05-19|

In summary, the oldest feature in the Star War universe is Yoda, who is a humanoid alien. He has appeared in 5 films, with titles *The Empire Strikes Back*, *Return of the Jedi*, *The Phantom Menace*, *Attack of the Clones* and *Revenge of the Sith*.
