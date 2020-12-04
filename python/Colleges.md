# Colleges.py - Methods

```python
import math
import csv
import sys

def distance(origin, destination):
    """
    Calculate the Haversine distance.
    From: https://stackoverflow.com/a/38187562/1561431
    Parameters
    ----------
    origin : tuple of float
        (lat, long)
    destination : tuple of float
        (lat, long)
    Returns
    -------
    distance_in_km : float
    Examples
    --------
    >>> origin = (48.1372, 11.5756)  # Munich
    >>> destination = (52.5186, 13.4083)  # Berlin
    >>> round(distance(origin, destination), 1)
    504.2
    """
    lat1, lon1 = origin
    lat2, lon2 = destination
    radius = 6371  # km

    dlat = math.radians(lat2 - lat1)
    dlon = math.radians(lon2 - lon1)
    a = (math.sin(dlat / 2) * math.sin(dlat / 2) +
         math.cos(math.radians(lat1)) * math.cos(math.radians(lat2)) *
         math.sin(dlon / 2) * math.sin(dlon / 2))
    c = 2 * math.atan2(math.sqrt(a), math.sqrt(1 - a))
    d = radius * c

    return d

def closest_university(location):
    """
    Finds the closest university to location. location is a tuple
    with latitude and longitude, in that order, for the location
    you're searching from.
    This method should return a tuple with the distance and
    university name.
    """

    csv_file = csv.DictReader(open('university-data.csv', 'r', encoding="utf-8"))

    closest = sys.float_info.max
    name = ""
    for row in csv_file:
        if row['LATITUDE'] == '-' or row['LONGITUDE'] == '-':
            continue
        loc = (float(row['LATITUDE']), float(row['LONGITUDE']))
        dist = distance(location, loc)
        if dist < closest:
            closest = dist
            name = row['INSTNM']

    return (closest, name)

def state_count(state):
    """
    Returns the number of times a college or university in state is found.
    You're going to want to use the STABBR field and can assume that it's
    case sensitive and will always be the 2 character abbreviation for a
    state
    """
    csv_file = csv.DictReader(open('university-data.csv', 'r', encoding="utf-8"))
    
    k = 0
    for row in csv_file:
        if row['STABBR'] == state:
            k += 1

    return k
    
def highest_in_state(state):
    """
    Returns the name and cost of the most expensive university in state
    We're using the TUITIONFEE_IN field as cost and INSTNM as the school
    name.
    Be careful on data types on this one. 
    """

    csv_file = csv.DictReader(open('university-data.csv', 'r', encoding="utf-8"))

    highest = 0
    name = ""
    for row in csv_file:
        if row['STABBR'] == state and row['TUITIONFEE_IN'].isnumeric() and int(row['TUITIONFEE_IN']) > highest:
            highest = int(row['TUITIONFEE_IN'])
            name = row['INSTNM']

    return (highest, name)
```

# College Search CSV

## state_count
`state_count` needs to parse the `university-data.csv` file and return the number of times that `state` matches the `STABBR` field.

## highest_in_state
`highest_in_state` also has a `state` parameter, but this time it's going to return the highest in state tuition for that state along with the name of the highest cost institution as a tuple.

## closest_university
For `closest_university` you're going to determine the closest university to a give latitude and longitude pair.

To help you out there's a `distance` method given to you in the `closest_university.py` file. This method uses the Haversine forumla to determine the distance between to points accounting for the radius of the Earth.

In the `closest_university` function, given `location` as a tuple containing latitude and longitude, you're going to find the closest university to that point. Your return value will be a tuple containing the calculated distance followed by the institution name.
