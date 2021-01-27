# Students.py - Class

```python
import json

class Students():

    def universities(self):
        universities = []
        with open('students.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for student in data:
                if student['university'] not in universities:
                    universities.append(student['university'])
        return universities

    def university_count(self):
        return len(self.universities())

    def average_gpa(self):
        k = 0
        sum = 0.0
        with open('students.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for student in data:
                k += 1
                sum += student['gpa']
        return sum / k

    def university_average(self, university_name):
        k = 0
        sum = 0.0
        with open('students.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for student in data:
                if student['university'] == university_name:
                    k += 1
                    sum += student['gpa']
        return sum / k if k > 0 else 0.0

    def highest_average(self):
        gpas = {}
        with open('students.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for student in data:
                if student['university'] not in gpas:
                    gpas[student['university']] = [1, student['gpa']]
                else:
                    gpas[student['university']][0] += 1
                    gpas[student['university']][1] += student['gpa']
        largest = ('', 0.0)
        for key, value in gpas.items():
            average = value[1] / value[0]
            if average > largest[1]:
                largest = (key, average)
        return { 'school': largest[0], 'average': largest[1] }


    def highest_student_gpa(self, how_many):
        top = []
        with open('students.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for student in data:
                gpa = student['gpa']
                last_name = student['last_name']
                first_name = student['first_name']
                if len(top) == 0:
                    top.append(student)
                else:
                    for i in range(len(top)):
                        if gpa > top[i]['gpa']:
                            top.insert(i, student)
                            break
                        elif gpa == top[i]['gpa']:
                            if last_name < top[i]['last_name']:
                                top.insert(i, student)
                                break
                            elif last_name == top[i]['last_name']:
                                if first_name <= top[i]['first_name']:
                                    top.insert(i, student)
                                    break
                                else:
                                    continue
                            else:
                                continue
                    if len(top) < how_many:
                        top.append(student)
                    elif len(top) > how_many:
                        del top[how_many:]
        return top

    def find_students(self, name):
        arr = []
        with open('students.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for student in data:
                last_name = student['last_name']
                first_name = student['first_name']
                if name.lower() not in last_name.lower() and name.lower() not in first_name.lower():
                    continue
                if len(arr) == 0:
                    arr.append(student)
                else:
                    gpa = student['gpa']
                    for i in range(len(arr)):
                        if gpa > arr[i]['gpa']:
                            arr.insert(i, student)
                            break
                        elif gpa == arr[i]['gpa']:
                            if last_name < arr[i]['last_name']:
                                arr.insert(i, student)
                                break
                            elif last_name == arr[i]['last_name']:
                                if first_name <= arr[i]['first_name']:
                                    arr.insert(i, student)
                                    break
                                else:
                                    continue
                            else:
                                continue
                        elif gpa < arr[i]['gpa'] and i == len(arr) - 1:
                            arr.append(student)
        return arr
```

## Student GPA Search
For this lab you're going to be working with a JSON file that contains GPA information on students that have been accepted into various universities.

### Data
The file `students.json` is a JSON file with an array of dictionary objects in the following format.

```json
{
    "last_name": "Last name of the student",
    "first_name": "First name of the student",
    "gender": "Either M or F",
    "gpa": 1.234,
    "university": "University student was accepted in to"
}
```

### Methods

#### university_count
`university_count` should return a count of distinct universities in the data set.

#### average_gpa
`average_gpa` should return the average GPA of all students in the data set. 

#### university_average
`university_average` should return the average GPA of all students accepted to `university_name`.
If there are no records that match `university_name` this method should return `0.0`.

#### highest_average
`highest_average` returns a dictionary with the name of the university with the highest GPA average and that average.

```json
{
    "school": "name of school with highest GPA average",
    "average": 1.2345
}
```

#### highest_student_gpa
The `highest_student_gpa` method should return a list of `how_many` of the highest scoring students.
This list should be sorted, first on `gpa` from highest to lowest and then on `last_name` followed by `first_name` alphabetically. 

#### find_students
`find_students` returns a list of all students in the data set that match `name`. 
A student is considered a "match" if `name` is any part of either their first or last name, case insensitive.
Like the previous method, this list should be sorted first on GPA in descending order followed by last and first name in ascending order. 
