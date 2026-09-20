## 1. Variables — 10 examples

### 1.1 Number variable

```gsve
define age = 19;
print(age);
```

### 1.2 Decimal variable

```gsve
define price = 149.99;
print(price);
```

### 1.3 String variable

```gsve
define name = "greenServe";
print(name);
```

### 1.4 Boolean variable

```gsve
define enabled = true;
print(enabled);
```

### 1.5 Null variable

```gsve
define result = null;
print(result);
```

### 1.6 Multiple variables

```gsve
define name = "server";
define port = 8080;
define secure = true;

print(name);
print(port);
print(secure);
```

### 1.7 Reassign a variable

```gsve
define count = 10;

count = 20;
print(count);
```

### 1.8 Arithmetic assignment

```gsve
define total = 100;

total = total + 50;
total = total * 2;

print(total);
```

### 1.9 String concatenation

```gsve
define first = "green";
define second = "Serve";

define name = first + second;

print(name);
```

### 1.10 Variables with expressions

```gsve
define width = 20;
define height = 10;

define area = width * height;

print(area);
```

---

# 2. `if` / `else` — 10 examples

### 2.1 Simple if

```gsve
define age = 19;

if (age >= 18) {
    print("adult");
}
```

### 2.2 If else

```gsve
define age = 16;

if (age >= 18) {
    print("adult");
} else {
    print("minor");
}
```

### 2.3 Number comparison

```gsve
define score = 85;

if (score >= 80) {
    print("high score");
} else {
    print("normal score");
}
```

### 2.4 Equality

```gsve
define status = "active";

if (status == "active") {
    print("running");
} else {
    print("stopped");
}
```

### 2.5 Not equal

```gsve
define status = "offline";

if (status != "online") {
    print("connection unavailable");
} else {
    print("connected");
}
```

### 2.6 Logical AND

```gsve
define age = 25;
define verified = true;

if (age >= 18 && verified) {
    print("access granted");
} else {
    print("access denied");
}
```

### 2.7 Logical OR

```gsve
define admin = false;
define owner = true;

if (admin || owner) {
    print("authorized");
} else {
    print("unauthorized");
}
```

### 2.8 Nested if

```gsve
define age = 25;
define active = true;

if (age >= 18) {
    if (active) {
        print("adult account is active");
    } else {
        print("adult account is inactive");
    }
} else {
    print("underage account");
}
```

### 2.9 Conditional assignment

```gsve
define score = 90;
define grade = "F";

if (score >= 80) {
    grade = "A";
} else {
    grade = "B";
}

print(grade);
```

### 2.10 Multiple nested conditions

```gsve
define temperature = 30;

if (temperature > 35) {
    print("hot");
} else {
    if (temperature >= 20) {
        print("warm");
    } else {
        print("cold");
    }
}
```

---

# 3. `for` loops — 10 examples

### 3.1 Array iteration

```gsve
define numbers = [1, 2, 3, 4, 5];

for (number in numbers) {
    print(number);
}
```

### 3.2 String array

```gsve
define names = ["Alice", "Bob", "Charlie"];

for (name in names) {
    print(name);
}
```

### 3.3 Sum an array

```gsve
define numbers = [10, 20, 30];
define total = 0;

for (number in numbers) {
    total = total + number;
}

print(total);
```

### 3.4 Count elements

```gsve
define numbers = [5, 10, 15, 20];
define count = 0;

for (number in numbers) {
    count = count + 1;
}

print(count);
```

### 3.5 Filter values

```gsve
define numbers = [10, 25, 5, 40, 15];

for (number in numbers) {
    if (number >= 20) {
        print(number);
    } else {
        print("small");
    }
}
```

### 3.6 Nested for loops

```gsve
define rows = [1, 2, 3];
define columns = [10, 20];

for (row in rows) {
    for (column in columns) {
        print(row * column);
    }
}
```

### 3.7 Break

```gsve
define numbers = [1, 2, 3, 4, 5];

for (number in numbers) {
    if (number == 4) {
        break;
    } else {
        print(number);
    }
}
```

### 3.8 Continue

```gsve
define numbers = [1, 2, 3, 4, 5];

for (number in numbers) {
    if (number == 3) {
        continue;
    } else {
        print(number);
    }
}
```

### 3.9 Object keys

```gsve
define user = {
    name: "Dominex",
    language: "greenServe",
    version: 1
};

for (key in user) {
    print(key);
}
```

### 3.10 Array of objects

```gsve
define products = [
    { name: "Phone", price: 500 },
    { name: "Laptop", price: 1000 },
    { name: "Tablet", price: 300 }
];

for (product in products) {
    print(product.name);
    print(product.price);
}
```

---

# 4. `while` loops — 10 examples

### 4.1 Basic counter

```gsve
define count = 0;

while (count < 5) {
    print(count);
    count = count + 1;
}
```

### 4.2 Countdown

```gsve
define count = 5;

while (count > 0) {
    print(count);
    count = count - 1;
}
```

### 4.3 Sum numbers

```gsve
define number = 1;
define total = 0;

while (number <= 10) {
    total = total + number;
    number = number + 1;
}

print(total);
```

### 4.4 Multiplication

```gsve
define number = 1;
define total = 1;

while (number <= 5) {
    total = total * number;
    number = number + 1;
}

print(total);
```

### 4.5 While with if

```gsve
define number = 1;

while (number <= 10) {
    if (number % 2 == 0) {
        print(number);
    } else {
        print("odd");
    }

    number = number + 1;
}
```

### 4.6 Break in while

```gsve
define count = 0;

while (true) {
    count = count + 1;

    if (count == 5) {
        break;
    } else {
        print(count);
    }
}
```

### 4.7 Continue in while

```gsve
define count = 0;

while (count < 6) {
    count = count + 1;

    if (count == 3) {
        continue;
    } else {
        print(count);
    }
}
```

### 4.8 Nested while

```gsve
define outer = 1;

while (outer <= 3) {
    define inner = 1;

    while (inner <= 2) {
        print(outer * inner);
        inner = inner + 1;
    }

    outer = outer + 1;
}
```

### 4.9 Building a value

```gsve
define count = 1;
define result = "";

while (count <= 5) {
    result = result + str(count);
    count = count + 1;
}

print(result);
```

### 4.10 Until threshold

```gsve
define total = 0;

while (total < 100) {
    total = total + 25;
}

print(total);
```

---

# 5. Functions — 10 examples

### 5.1 Simple function

```gsve
func hello() {
    print("Hello from greenServe");
}

hello();
```

### 5.2 One parameter

```gsve
func greet(name) {
    print("Hello " + name);
}

greet("Dominex");
```

### 5.3 Two parameters

```gsve
func add(a, b) {
    print(a + b);
}

add(10, 20);
```

### 5.4 Function returning a value

```gsve
func add(a, b) {
    return a + b;
}

define result = add(5, 7);

print(result);
```

### 5.5 Function with if

```gsve
func checkAge(age) {
    if (age >= 18) {
        return "adult";
    } else {
        return "minor";
    }
}

print(checkAge(19));
```

### 5.6 Function with loop

```gsve
func sum(numbers) {
    define total = 0;

    for (number in numbers) {
        total = total + number;
    }

    return total;
}

define values = [10, 20, 30];

print(sum(values));
```

### 5.7 Function calling another function

```gsve
func double(number) {
    return number * 2;
}

func quadruple(number) {
    return double(double(number));
}

print(quadruple(5));
```

### 5.8 Multiple parameters

```gsve
func createMessage(name, language, version) {
    return name + " uses " + language + " " + str(version);
}

print(createMessage("server", "greenServe", 1));
```

### 5.9 Function modifying an object

```gsve
func activate(user) {
    user.active = true;
    return user;
}

define user = {
    name: "Dominex",
    active: false
};

define result = activate(user);

print(result.active);
```

### 5.10 Function with nested loop

```gsve
func multiplyAll(values, factor) {
    define total = 0;

    for (value in values) {
        total = total + value * factor;
    }

    return total;
}

define numbers = [2, 4, 6];

print(multiplyAll(numbers, 10));
```

---

# 6. `return` — 10 examples

### 6.1 Return number

```gsve
func getNumber() {
    return 100;
}

print(getNumber());
```

### 6.2 Return string

```gsve
func getName() {
    return "greenServe";
}

print(getName());
```

### 6.3 Return boolean

```gsve
func isActive() {
    return true;
}

print(isActive());
```

### 6.4 Return from if

```gsve
func check(number) {
    if (number > 10) {
        return "large";
    } else {
        return "small";
    }
}

print(check(20));
```

### 6.5 Return arithmetic

```gsve
func calculate(a, b) {
    return a * b + 10;
}

print(calculate(5, 4));
```

### 6.6 Return array

```gsve
func numbers() {
    return [10, 20, 30];
}

define values = numbers();

print(values);
```

### 6.7 Return object

```gsve
func createUser() {
    return {
        name: "Dominex",
        active: true
    };
}

define user = createUser();

print(user.name);
```

### 6.8 Return from loop condition

```gsve
func findLarge(values) {
    for (value in values) {
        if (value > 50) {
            return value;
        } else {
            print("checking");
        }
    }

    return null;
}

define values = [10, 20, 75, 90];

print(findLarge(values));
```

### 6.9 Return function result

```gsve
func add(a, b) {
    return a + b;
}

func calculate(a, b) {
    return add(a, b) * 2;
}

print(calculate(5, 10));
```

### 6.10 Return early

```gsve
func validate(age) {
    if (age < 0) {
        return "invalid";
    } else {
        if (age >= 18) {
            return "allowed";
        } else {
            return "restricted";
        }
    }
}

print(validate(19));
```

---

# 7. Arrays — 10 examples

### 7.1 Basic array

```gsve
define numbers = [1, 2, 3, 4, 5];

print(numbers);
```

### 7.2 Array indexing

```gsve
define numbers = [10, 20, 30];

print(numbers[0]);
print(numbers[1]);
print(numbers[2]);
```

### 7.3 Change array element

```gsve
define numbers = [10, 20, 30];

numbers[1] = 99;

print(numbers);
```

### 7. Add an indexed element

```gsve
define numbers = [10, 20];

numbers[2] = 30;
numbers[3] = 40;

print(numbers);
```

### 7. Array length

```gsve
define names = ["Alice", "Bob", "Charlie"];

print(len(names));
```

### 7. Array loop

```gsve
define names = ["Alice", "Bob", "Charlie"];

for (name in names) {
    print(name);
}
```

### 7. Nested arrays

```gsve
define matrix = [
    [1, 2],
    [3, 4],
    [5, 6]
];

print(matrix[0][0]);
print(matrix[2][1]);
```

### 7. Array of objects

```gsve
define users = [
    { name: "Alice", age: 20 },
    { name: "Bob", age: 25 }
];

print(users[0].name);
print(users[1].age);
```

### 7. Array calculations

```gsve
define prices = [100, 200, 300];
define total = 0;

for (price in prices) {
    total = total + price;
}

print(total);
```

### 7. Mixed array

```gsve
define values = [
    10,
    "greenServe",
    true,
    null
];

print(values[0]);
print(values[1]);
print(values[2]);
print(values[3]);
```

---

# 8. Objects — 10 examples

### 8.1 Basic object

```gsve
define user = {
    name: "Dominex",
    age: 19
};

print(user);
```

### 8.2 Object member access

```gsve
define user = {
    name: "Dominex",
    age: 19
};

print(user.name);
print(user.age);
```

### 8.3 Change object property

```gsve
define user = {
    name: "Dominex",
    active: false
};

user.active = true;

print(user.active);
```

### 8.4 Nested object

```gsve
define user = {
    name: "Dominex",
    profile: {
        language: "greenServe",
        version: 1
    }
};

print(user.profile.language);
```

### 8.5 Object indexing

```gsve
define user = {
    name: "Dominex",
    age: 19
};

print(user["name"]);
print(user["age"]);
```

### 8.6 Object property assignment by index

```gsve
define user = {
    name: "Dominex"
};

user["age"] = 19;

print(user.age);
```

### 8.7 Object length

```gsve
define server = {
    host: "localhost",
    port: 8080,
    secure: true
};

print(len(server));
```

### 8.8 Iterate object keys

```gsve
define config = {
    host: "localhost",
    port: 8080,
    debug: true
};

for (key in config) {
    print(key);
}
```

### 8.9 Object passed to function

```gsve
func showUser(user) {
    print(user.name);
    print(user.age);
}

define user = {
    name: "Dominex",
    age: 19
};

showUser(user);
```

### 8.10 Object returned from function

```gsve
func serverConfig() {
    return {
        host: "127.0.0.1",
        port: 8080,
        secure: false
    };
}

define config = serverConfig();

print(config.host);
print(config.port);
```

---

# 9. Operators and expressions — 10 examples

### 9.1 Addition

```gsve
define result = 10 + 20;

print(result);
```

### 9.2 Subtraction

```gsve
define result = 50 - 15;

print(result);
```

### 9.3 Multiplication

```gsve
define result = 8 * 5;

print(result);
```

### 9.4 Division

```gsve
define result = 100 / 4;

print(result);
```

### 9.5 Modulo

```gsve
define result = 17 % 5;

print(result);
```

### 9.6 Operator precedence

```gsve
define result = 10 + 5 * 2;

print(result);
```

### 9.7 Parentheses

```gsve
define result = (10 + 5) * 2;

print(result);
```

### 9.8 Comparisons

```gsve
define a = 10;
define b = 20;

print(a < b);
print(a <= b);
print(a > b);
print(a >= b);
```

### 9.9 Equality

```gsve
define a = 10;
define b = 10;

print(a == b);
print(a != b);
```

### 9.10 Logical expressions

```gsve
define age = 25;
define active = true;

define allowed = age >= 18 && active;

print(allowed);
```

---

# 10. Built-in functions and types — 10 examples

### 10.1 `print`

```gsve
print("Hello");
print(100);
print(true);
```

### 10.2 `show`

```gsve
show("greenServe");
show(123);
```

### 10.3 `len` with string

```gsve
define text = "greenServe";

print(len(text));
```

### 10.4 `len` with array

```gsve
define numbers = [10, 20, 30, 40];

print(len(numbers));
```

### 10.5 `len` with object

```gsve
define user = {
    name: "Dominex",
    age: 19
};

print(len(user));
```

### 10.6 `str`

```gsve
define number = 123;

define text = str(number);

print(text);
print(type(text));
```

### 10.7 `num`

```gsve
define text = "456";

define number = num(text);

print(number);
print(type(number));
```

### 10.8 `type`

```gsve
define number = 10;
define text = "hello";
define flag = true;
define values = [1, 2, 3];

print(type(number));
print(type(text));
print(type(flag));
print(type(values));
```

### 10.9 Combining built-ins

```gsve
define numbers = [10, 20, 30];

print("count = " + str(len(numbers)));
print("type = " + type(numbers));
```

### 10.10 Built-ins in a function

```gsve
func describe(value) {
    print("type:");
    print(type(value));
    print("value:");
    print(str(value));
}

describe(100);
describe("greenServe");
describe([1, 2, 3]);
```

---

# 11. Nested control flow — 10 examples

### 11.1 If inside for

```gsve
define numbers = [1, 2, 3, 4, 5];

for (number in numbers) {
    if (number % 2 == 0) {
        print("even");
    } else {
        print("odd");
    }
}
```

### 11.2 If inside while

```gsve
define number = 0;

while (number < 5) {
    if (number == 2) {
        print("middle");
    } else {
        print(number);
    }

    number = number + 1;
}
```

### 11.3 For inside while

```gsve
define count = 0;

while (count < 3) {
    define values = [1, 2, 3];

    for (value in values) {
        print(value);
    }

    count = count + 1;
}
```

### 11.4 While inside for

```gsve
define values = [2, 3, 4];

for (value in values) {
    define count = 0;

    while (count < value) {
        print(count);
        count = count + 1;
    }
}
```

### 11.5 Nested if

```gsve
define user = {
    active: true,
    admin: true
};

if (user.active) {
    if (user.admin) {
        print("admin");
    } else {
        print("user");
    }
} else {
    print("inactive");
}
```

### 11.6 Nested loops

```gsve
define a = [1, 2, 3];
define b = [4, 5, 6];

for (x in a) {
    for (y in b) {
        print(x + y);
    }
}
```

### 11.7 Loop with function call

```gsve
func square(number) {
    return number * number;
}

define numbers = [1, 2, 3, 4];

for (number in numbers) {
    print(square(number));
}
```

### 11.8 Loop with return function

```gsve
func find(values) {
    for (value in values) {
        if (value > 50) {
            return value;
        } else {
            print("not found yet");
        }
    }

    return null;
}

define values = [10, 20, 80, 90];

print(find(values));
```

### 11.9 Nested object processing

```gsve
define company = {
    name: "greenServe",
    teams: [
        { name: "server", size: 5 },
        { name: "runtime", size: 3 }
    ]
};

for (team in company.teams) {
    if (team.size > 3) {
        print(team.name);
    } else {
        print("small team");
    }
}
```

### 11.10 Complete control-flow example

```gsve
define products = [
    { name: "Phone", price: 500 },
    { name: "Laptop", price: 1000 },
    { name: "Tablet", price: 300 }
];

define total = 0;

func add(a, b) {
    return a + b;
}

for (product in products) {
    if (product.price > 400) {
        total = add(total, product.price);
    } else {
        total = total + 1;
    }
}

while (total < 2000) {
    total = total + 100;
}

print(total);
```

---

# 12. Imports / C modules — 10 examples

These specifically correspond to the interpreter's `.so` module system. The module must already be installed in one of the system module directories used by `evaluator.c`.

### 12.1 Import `gsnum`

```gsve
import gsnum;

print(gsnum);
```

### 12.2 Import and call a module function

```gsve
import gsnum;

define result = gsnum.add(10, 20);

print(result);
```

### 12.3 Import vector module

```gsve
import gsvector;

define values = [3, 4];

print(gsvector.norm(values));
```

### 12.4 Import random module

```gsve
import gsrandom;

print(gsrandom);
```

### 12.5 Import tokenizer module

```gsve
import gstoken;

print(gstoken);
```

### 12.6 Import vocabulary module

```gsve
import gsvocab;

define words = gsvocab.words("greenServe programming language");

print(words);
```

### 12.7 `from ... import`

```gsve
from gsnum import add;

print(add(10, 20));
```

### 12.8 Multiple imported functions

```gsve
from gsnum import add, subtract;

define total = add(100, 50);
define result = subtract(total, 25);

print(result);
```

### 12.9 Vector functions

```gsve
from gsvector import dot, norm;

define a = [1, 2, 3];
define b = [4, 5, 6];

print(dot(a, b));
print(norm(a));
```

### 12.10 Module + normal language features

```gsve
from gsnum import add;

define numbers = [10, 20, 30];
define total = 0;

for (number in numbers) {
    total = add(total, number);
}

if (total >= 60) {
    print("total is large");
} else {
    print("total is small");
}
```

---

## 13. More complete real-world-style examples — 10

### 13.1 Product total

```gsve
define products = [
    { name: "Phone", price: 500 },
    { name: "Laptop", price: 1000 },
    { name: "Tablet", price: 300 }
];

define total = 0;

for (product in products) {
    total = total + product.price;
}

print(total);
```

### 13.2 Product filtering

```gsve
define products = [
    { name: "Phone", price: 500 },
    { name: "Laptop", price: 1000 },
    { name: "Tablet", price: 300 }
];

for (product in products) {
    if (product.price >= 500) {
        print(product.name);
    } else {
        print("below limit");
    }
}
```

### 13.3 User validation

```gsve
func validateUser(user) {
    if (user.name == "") {
        return false;
    } else {
        if (user.age >= 18) {
            return true;
        } else {
            return false;
        }
    }
}

define user = {
    name: "Dominex",
    age: 19
};

print(validateUser(user));
```

### 13.4 Shopping cart

```gsve
define cart = [
    { name: "Keyboard", price: 50 },
    { name: "Mouse", price: 25 },
    { name: "Monitor", price: 200 }
];

define total = 0;

for (item in cart) {
    total = total + item.price;
}

print("Cart total: " + str(total));
```

### 13.5 Counter

```gsve
define numbers = [1, 2, 3, 4, 5, 6];
define even = 0;
define odd = 0;

for (number in numbers) {
    if (number % 2 == 0) {
        even = even + 1;
    } else {
        odd = odd + 1;
    }
}

print(even);
print(odd);
```

### 13.6 Factorial

```gsve
func factorial(number) {
    define result = 1;

    while (number > 1) {
        result = result * number;
        number = number - 1;
    }

    return result;
}

print(factorial(5));
```

### 13.7 Search

```gsve
func contains(values, target) {
    for (value in values) {
        if (value == target) {
            return true;
        } else {
            print("checking");
        }
    }

    return false;
}

define values = [10, 20, 30, 40];

print(contains(values, 30));
```

### 13.8 Simple configuration

```gsve
define config = {
    host: "127.0.0.1",
    port: 8080,
    debug: true
};

if (config.debug) {
    print("debug enabled");
} else {
    print("debug disabled");
}

print(config.host);
print(config.port);
```

### 13.9 Matrix processing

```gsve
define matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

define total = 0;

for (row in matrix) {
    for (value in row) {
        total = total + value;
    }
}

print(total);
```

### 13.10 Full language combination

```gsve
define products = [
    { name: "Phone", price: 500 },
    { name: "Laptop", price: 1000 },
    { name: "Tablet", price: 300 }
];

func add(a, b) {
    return a + b;
}

func calculate(products) {
    define total = 0;

    for (product in products) {
        if (product.price >= 500) {
            total = add(total, product.price);
        } else {
            total = total + 1;
        }
    }

    while (total < 2000) {
        total = total + 100;
    }

    return total;
}

define result = calculate(products);

print(result);
```
