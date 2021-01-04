# Math.py - Server

```python
import flask
from flask import request
import json
import random
import math

app = flask.Flask(__name__)


@app.route('/area/square', methods=['GET'])
def area_square():
    if 's' not in request.args:
        return 'Missing parameter', 400
    if not request.args['s'].isdigit():
        return 'Invalid parameter', 400
    s = int(request.args['s'])
    ret = {
        'a': s*s,
        's': s
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/area/rectangle', methods=['GET'])
def area_rectangle():
    missing = 'l' not in request.args or 'w' not in request.args
    if missing:
        return 'Missing parameter', 400
    invalid = not request.args['l'].isdigit() or not request.args['w'].isdigit()
    if invalid:
        return 'Invalid parameter', 400
    l = int(request.args['l'])
    w = int(request.args['w'])
    ret = {
        'a': l*w,
        'l': l,
        'w': w
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/area/triangle', methods=['GET'])
def area_triangle():
    missing = 'b' not in request.args or 'h' not in request.args
    if missing:
        return 'Missing parameter', 400
    invalid = not request.args['b'].isdigit() or not request.args['h'].isdigit()
    if invalid:
        return 'Invalid parameter', 400
    b = int(request.args['b'])
    h = int(request.args['h'])
    ret = {
        'a': b*h/2,
        'b': b,
        'h': h
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/area/heron', methods=['GET'])
def area_heron():
    missing = 'x' not in request.args or 'y' not in request.args or 'z' not in request.args
    if missing:
        return 'Missing parameter', 400
    invalid = not request.args['x'].isdigit() or not request.args['y'].isdigit() or not request.args['z'].isdigit()
    if invalid:
        return 'Invalid parameter', 400
    x = int(request.args['x'])
    y = int(request.args['y'])
    z = int(request.args['z'])
    s = (x + y + z) / 2
    a = math.sqrt(s*(s-x)*(s-y)*(s-z))
    ret = {
        'a': a,
        'x': x,
        'y': y,
        'z': z,
        's': s
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/area/parallelogram', methods=['GET'])
def area_parallelogram():
    missing = 'b' not in request.args or 'h' not in request.args
    if missing:
        return 'Missing parameter', 400
    invalid = not request.args['b'].isdigit() or not request.args['h'].isdigit()
    if invalid:
        return 'Invalid parameter', 400
    b = int(request.args['b'])
    h = int(request.args['h'])
    ret = {
        'a': b*h,
        'b': b,
        'h': h
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/area/circle', methods=['GET'])
def area_circle():
    if 'r' not in request.args:
        return 'Missing parameter', 400
    if not request.args['r'].isdigit():
        return 'Invalid parameter', 400
    r = int(request.args['r'])
    ret = {
        'a': r*r*math.pi,
        'r': r
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/area/trapezoid', methods=['GET'])
def area_trapezoid():
    missing = 'b1' not in request.args or 'b2' not in request.args or 'h' not in request.args
    if missing:
        return 'Missing parameter', 400
    invalid = not request.args['b1'].isdigit() or not request.args['b2'].isdigit() or not request.args['h'].isdigit()
    if invalid:
        return 'Invalid parameter', 400
    b1 = int(request.args['b1'])
    b2 = int(request.args['b2'])
    h = int(request.args['h'])
    ret = {
        'a': (b1+b2)/2*h,
        'b1': b1,
        'b2': b2,
        'h': h,
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/surface/cube', methods=['GET'])
def surface_cube():
    if 's' not in request.args:
        return 'Missing parameter', 400
    if not request.args['s'].isdigit():
        return 'Invalid parameter', 400
    s = int(request.args['s'])
    ret = {
        'sa': 6*s*s,
        's': s
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/surface/sphere', methods=['GET'])
def surface_sphere():
    if 'r' not in request.args:
        return 'Missing parameter', 400
    if not request.args['r'].isdigit():
        return 'Invalid parameter', 400
    r = int(request.args['r'])
    ret = {
        'sa': 4*math.pi*r*r,
        'r': r
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/surface/cylinder', methods=['GET'])
def surface_cylinder():
    if 'r' not in request.args or 'h' not in request.args:
        return 'Missing parameter', 400
    if not request.args['r'].isdigit() or not request.args['h'].isdigit():
        return 'Invalid parameter', 400
    r = int(request.args['r'])
    h = int(request.args['h'])
    ret = {
        'sa': 2*math.pi*r*h,
        'r': r,
        'h': h
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/perimeter/square', methods=['GET'])
def perimeter_square():
    if 's' not in request.args:
        return 'Missing parameter', 400
    if not request.args['s'].isdigit():
        return 'Invalid parameter', 400
    s = int(request.args['s'])
    ret = {
        'p': 4*s,
        's': s
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/perimeter/rectangle', methods=['GET'])
def perimeter_rectangle():
    if 'l' not in request.args or 'w' not in request.args:
        return 'Missing parameter', 400
    if not request.args['l'].isdigit() or not request.args['w'].isdigit():
        return 'Invalid parameter', 400
    l = int(request.args['l'])
    w = int(request.args['w'])
    ret = {
        'p': 2*l+2*w,
        'l': l,
        'w': w
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/perimeter/triangle', methods=['GET'])
def perimeter_triangle():
    if 's1' not in request.args or 's2' not in request.args or 's3' not in request.args:
        return 'Missing parameter', 400
    if not request.args['s1'].isdigit() or not request.args['s2'].isdigit() or not request.args['s3'].isdigit():
        return 'Invalid parameter', 400
    s1 = int(request.args['s1'])
    s2 = int(request.args['s2'])
    s3 = int(request.args['s3'])
    ret = {
        'p': s1+s2+s3,
        's1': s1,
        's2': s2,
        's3': s3
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/perimeter/circle', methods=['GET'])
def perimeter_circle():
    if 'd' not in request.args:
        return 'Missing parameter', 400
    if not request.args['d'].isdigit():
        return 'Invalid parameter', 400
    d = int(request.args['d'])
    ret = {
        'p': math.pi*d,
        'd': d
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/volume/cube', methods=['GET'])
def volume_cube():
    if 's' not in request.args:
        return 'Missing parameter', 400
    if not request.args['s'].isdigit():
        return 'Invalid parameter', 400
    s = int(request.args['s'])
    ret = {
        'v': s*s*s,
        's': s
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/volume/prism', methods=['GET'])
def volume_prism():
    if 'l' not in request.args or 'w' not in request.args or 'h' not in request.args:
        return 'Missing parameter', 400
    if not request.args['l'].isdigit() or not request.args['w'].isdigit() or not request.args['h'].isdigit():
        return 'Invalid parameter', 400
    l = int(request.args['l'])
    w = int(request.args['w'])
    h = int(request.args['h'])
    ret = {
        'p': l*w*h,
        'l': l,
        'w': w,
        'h': h
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/volume/pyramid', methods=['GET'])
def volume_pyramid():
    missing = 'b' not in request.args or 'h' not in request.args
    if missing:
        return 'Missing parameter', 400
    invalid = not request.args['b'].isdigit() or not request.args['h'].isdigit()
    if invalid:
        return 'Invalid parameter', 400
    b = int(request.args['b'])
    h = int(request.args['h'])
    ret = {
        'a': b*b*h/3,
        'b': b,
        'h': h
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/volume/cylinder', methods=['GET'])
def volume_cylinder():
    if 'r' not in request.args or 'h' not in request.args:
        return 'Missing parameter', 400
    if not request.args['r'].isdigit() or not request.args['h'].isdigit():
        return 'Invalid parameter', 400
    r = int(request.args['r'])
    h = int(request.args['h'])
    ret = {
        'v': math.pi*r*r*h,
        'r': r,
        'h': h
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/volume/cone', methods=['GET'])
def volume_cone():
    if 'r' not in request.args or 'h' not in request.args:
        return 'Missing parameter', 400
    if not request.args['r'].isdigit() or not request.args['h'].isdigit():
        return 'Invalid parameter', 400
    r = int(request.args['r'])
    h = int(request.args['h'])
    ret = {
        'v': math.pi*r*r*h/3,
        'r': r,
        'h': h
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/volume/sphere', methods=['GET'])
def volume_sphere():
    if 'r' not in request.args:
        return 'Missing parameter', 400
    if not request.args['r'].isdigit():
        return 'Invalid parameter', 400
    r = int(request.args['r'])
    ret = {
        'v': 4*math.pi*r*r*r/3,
        'r': r,
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/distance', methods=['GET'])
def distance():
    if 'x1' not in request.args or 'x2' not in request.args or 'y1' not in request.args or 'y2' not in request.args:
        return 'Missing parameter', 400
    if not request.args['x1'].isdigit() or not request.args['x2'].isdigit() or not request.args['y1'].isdigit() or not request.args['y2'].isdigit():
        return 'Invalid parameter', 400
    x1 = int(request.args['x1'])
    x2 = int(request.args['x2'])
    y1 = int(request.args['y1'])
    y2 = int(request.args['y2'])
    ret = {
        'd': math.sqrt((x2-x1)**2 + (y2-y1)**2),
        'x1': x1,
        'x2': x2,
        'y1': y1,
        'y2': y2
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/slope', methods=['GET'])
def slope():
    if 'x1' not in request.args or 'x2' not in request.args or 'y1' not in request.args or 'y2' not in request.args:
        return 'Missing parameter', 400
    if not request.args['x1'].isdigit() or not request.args['x2'].isdigit() or not request.args['y1'].isdigit() or not request.args['y2'].isdigit():
        return 'Invalid parameter', 400
    x1 = int(request.args['x1'])
    x2 = int(request.args['x2'])
    y1 = int(request.args['y1'])
    y2 = int(request.args['y2'])
    ret = {
        'm': (y2-y1)/(x2-x1),
        'x1': x1,
        'x2': x2,
        'y1': y1,
        'y2': y2
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/pythag', methods=['GET'])
def pythag():
    a = 'a' in request.args
    b = 'b' in request.args
    c = 'c' in request.args
    if a and b and not c:
        a = request.args['a']
        b = request.args['b']
        if not a.isdigit() or not b.isdigit():
            return 'Invalid parameter', 400
        a = int(a)
        b = int(b)
        ret = {
            'a': a,
            'b': b,
            'c': math.sqrt(a**2 + b**2),
        }
        return json.dumps(ret), 200, {'Content-Type': 'application/json'}
    elif b and c and not a:
        b = request.args['b']
        c = request.args['c']
        if not b.isdigit() or not c.isdigit():
            return 'Invalid parameter', 400
        b = int(b)
        c = int(c)
        ret = {
            'a': math.sqrt(c**2 - b**2),
            'b': b,
            'c': c,
        }
        return json.dumps(ret), 200, {'Content-Type': 'application/json'}
    elif a and c and not b:
        a = request.args['a']
        c = request.args['c']
        if not a.isdigit() or not c.isdigit():
            return 'Invalid parameter', 400
        a = int(a)
        c = int(c)
        ret = {
            'a': a,
            'b': math.sqrt(c**2 - a**2),
            'c': c,
        }
        return json.dumps(ret), 200, {'Content-Type': 'application/json'}
    elif a and b and c:
        a = request.args['a']
        b = request.args['b']
        c = request.args['c']
        if not a.isdigit() or not b.isdigit() or not c.isdigit():
            return 'Invalid parameter', 400
        ret = {
            'a': int(a),
            'b': int(b),
            'c': int(c),
        }
        if ret['c']**2 == ret['a']**2 + ret['b']**2:
            return json.dumps(ret), 200, {'Content-Type': 'application/json'}
        else:
            return 'Invalid triangle', 400
    else:
        return 'Missing parameter', 400


@app.route('/mean', methods=['GET'])
def mean():
    if 'nums' not in request.args:
        return 'Missing parameter', 400
    try:
        nums = request.args['nums'].split(',')
        for i in range(len(nums)):
            nums[i] = int(nums[i])
    except:
        return 'Invalid parameter', 400
    ret = {
        'mean': sum(nums) / len(nums),
        'nums': nums,
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/median', methods=['GET'])
def median():
    if 'nums' not in request.args:
        return 'Missing parameter', 400
    try:
        sorted = []
        nums = request.args['nums'].split(',')
        for i in range(len(nums)):
            nums[i] = int(nums[i])
            sorted.append(nums[i])
    except:
        return 'Invalid parameter', 400
    sorted.sort()
    median = None
    if len(sorted) % 2 == 1:
        median = sorted[int(len(sorted) / 2)]
    else:
        median = (sorted[int(len(sorted) / 2) - 1] + sorted[int(len(sorted) / 2)]) / 2
    ret = {
        'median': median,
        'nums': nums,
        'sorted': sorted
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.route('/mode', methods=['GET'])
def mode():
    if 'nums' not in request.args:
        return 'Missing parameter', 400
    try:
        nums = request.args['nums'].split(',')
        for i in range(len(nums)):
            nums[i] = int(nums[i])
    except:
        return 'Invalid parameter', 400
    occ = {}
    for x in nums:
        if x not in occ:
            occ[x] = 1
        else:
            occ[x] += 1
    largest = (None, 0)
    for x in occ.keys():
        if occ[x] > largest[1]:
            largest = (x, occ[x])
    ret = {
        'mode': largest[0],
        'nums': nums,
    }
    return json.dumps(ret), 200, {'Content-Type': 'application/json'}


@app.errorhandler(404)
def err_404(e):
    return 'Command not found', 404


app.run(host='127.0.0.1', port=3001)
```

## Math API Server

This time we're going to write an API server that solves math problems for us. Each route is a different formula to solve, and values will be passed as GET arguments.

Let's look at the area of a square route below. The route is listed as `/area/square` with one variable `s`. Calling `http://localhost:3001/area/square?s=10` should return JSON with the answer.  For that route the JSON returned would be.

```json
{
    "a": 100,
    "s": 10
}
```

Each route must return any variables passed and the solution. Use the letters in the formulas listed as keys.

Routes must also return their data with the `application/json` content type and a `200` status code header, assuming it was a good request. 

There are two "bad requests" that you also need to account for.
* Incorrect route. This needs to return a 404 status header. 
* Invalid or missing GET variables. This should return a 400 status header. This would be cases like `/area/square?x=10` where the variable is `x` instead of `s` or just calling `/area/square` without any variables. 
