# Jokes.py - Server

```python
import flask
from flask import request
import json
import random

app = flask.Flask(__name__)


@app.route('/', methods=['GET'])
def home():
    ret = {
        'success': True,
        'message': 'This is the home page'
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/random', methods=['GET'])
def rand():
    with open('dadjokes.json', 'r', encoding='UTF-8') as json_file:
        data = json.load(json_file)
        i = random.choice(data)
        return json.dumps(i), 200, {'Content-Type': 'application/json'}


@app.route('/joke', methods=['GET'])
def joke():
    if 'id' not in request.args:
        return 'Joke not found', 404
    with open('dadjokes.json', 'r', encoding='UTF-8') as json_file:
        data = json.load(json_file)
        for x in data:
            if x['id'] == request.args['id']:
                return json.dumps(x), 200, {'Content-Type': 'application/json'}
        return 'Joke not found', 404


@app.errorhandler(404)
def err_404(e):
    return 'Command not found', 404

app.run(host='127.0.0.1', port=3001)
```

## Dad Jokes API Server

### Routes
All routes should return an `application/json` content type and appropriate HTTP status code. 

#### Home
`/`
Must return JSON `{'success': True, 'message': 'This is the home page'}` with a `application/json` content type and a 200 status header.

#### Random Joke
`/random`
Should pull a random joke out of `dadjokes.json` and send it back to the browser. 

An example request may return the following JSON string.

```json
{
    "id": "b6dc0870",
    "name": "Color Blind",
    "joke": "Found out I was colour blind the other day... That one came right out the purple."
}
```

#### Specific Joke
`/joke`
This route allows you to request a specific joke from the data file by passing an `id` parameter. For example, if you want to get joke #123 the request would be `/joke?id=123`. 

`/joke?id=c9aaad4d` should return the following JSON string.

```json
{
    "id": "c9aaad4d",
    "name": "The Royal Flush Of The Jungle",
    "joke": "Why shouldn't you play cards in the jungle? Too many cheetahs."
}
```

You will need to check that the id parameter is there. If it is not, your server should return a 404 status header.

If the requested joke id is not in the data you should also send a 404 status header. 

### Credit
`dadjokes.json` came from [GitHub](https://github.com/mshwery/dad-jokes-api)
