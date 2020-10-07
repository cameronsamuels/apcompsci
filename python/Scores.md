## Scores.py - Class

```python
import json


class Scores():

    def most_tests(self):
        largest = ('', 0)
        with open('data.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for school in data['data']:
                if school[10].isnumeric() and int(school[10]) > largest[1]:
                    largest = (school[9], int(school[10]))
        return largest

    def best_score(self):
        largest = ('', 0)
        with open('data.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for school in data['data']:
                scores = school[11:14]
                for i in range(3):
                    if scores[i].isnumeric():
                        scores[i] = int(scores[i])
                    else:
                        scores[i] = 0
                if sum(scores) > largest[1]:
                    largest = (school[9], sum(scores))
        return largest

    def best_score_small(self):
        largest = ('', 0)
        with open('data.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for school in data['data']:
                if school[10].isnumeric() and int(school[10]) <= 50:
                    scores = school[11:14]
                    for i in range(3):
                        if scores[i].isnumeric():
                            scores[i] = int(scores[i])
                        else:
                            scores[i] = 0
                    if sum(scores) > largest[1]:
                        largest = (school[9], sum(scores))
        return largest

    def x_most_tests(self, x):
        descending = [('', 0)]
        with open('data.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for school in data['data']:
                if school[10].isnumeric():
                    val = int(school[10])
                    for i in range(len(descending)):
                        if val >= descending[i][1]:
                            descending.insert(i, (school[9], val))
                            break
        return descending[0:x]

    def x_highest_scores(self, x):
        descending = [('', 0)]
        with open('data.json', 'r', encoding='UTF-8') as json_file:
            data = json.load(json_file)
            for school in data['data']:
                scores = school[11:14]
                for i in range(3):
                    if scores[i].isnumeric():
                        scores[i] = int(scores[i])
                    else:
                        scores[i] = 0
                val = sum(scores)
                for i in range(len(descending)):
                    if val >= descending[i][1]:
                        descending.insert(i, (school[9], val))
                        break
        return descending[0:x]
```

## Most Tests
The most_tests method returns a tuple containing info on the school that gave the most SAT exams in 2012. First element should be the school name. Second element should be the number of exams given.

## Best Score
best_score returns a tuple containing school information on the school with the highest total SAT score (all 3 scores). First element should be the school name followed by the total score of all 3 tests.

## Best Score: Small Schools
The best_score_small is the same as best_score, but should only consider schools with no more than 50 total test takers.

## X Most Tests
x_most_tests should return an array of tuples containing the schools with the x most tests given in descending order. For example, if x is 10 then the method should return a 10 element list with the school giving the most tests in element 0, the school giving the 10th most tests in element 9, and the other going from 2nd to 9th in elements 1 through 8.

##  Highest Score
Same as x_most_tests, but this time return a list of the top x schools by total test score.
