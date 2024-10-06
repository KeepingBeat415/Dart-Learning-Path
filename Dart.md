### Variables

- Comments

```dart
// comments
/* comments */
```

- Booleans

```dart
bool isOn; // this is Booleans
bool isDog = false;

// generic object as "var"
var isOff = true;

// passing variable/function in the String
print('isOn = ${isOn}');
```

- Numbers

```dart
// Numbers generic type
num age = 0;

// Int
int people = 6;

// Double
double temp = 32.06;

// Parse an int
int test = int.parse('12');

int err = int.parse('12.09', onError: () => null);
print('err = ${err}');
```

- String

```dart
String hello = 'Hello World';
String name = 'Bryan Cairns';
// get a substring
String firstname = name.substring(0,5); // Bryan
// get the index of a string
int index = name.indexOf(' ');
String lastname = name.substring(index).trim();// Carins
//Length
print(name.length); // 11
//Contains
print(name.contains('#'));
//Create a list
List parts = name.split(' ');
print(parts); // Bryan Cairns
```

- Const Variables

```dart
const String txt = 'Hello World';
```

- User Input

```dart
stdout.write('What is your name?\r\n');
String name = stdin.readLineSync();

name.isEmpty ? stderr.write('Name is empty') : stdout.write('Hello ${name}\r\n');
```

### Collections

- Enum

```Dart
//Enum has to be declare outside of main function
enum colors {red, green, blue}
print(colors.values); // [colors.red, colors.green, colors.blue]
print(colors.red); // colors.red
```

- List

```Dart
List test = [1,2,3,4];
print(test.length);// 4
print(test[0]); // 1 => zero based index
print(test.elementAt[3]); // 4

//undeclared type
List things = new List();
things.add(1);
things.add('cats');
things.add(true);
print(things); // [1, cats, true]

//Generic type
List<int> numbers = new List<int>();
```

- Set

```Dart
// Set = unordered, not contain duplicates

Set<int> numbers = new Set<int>();
numbers.add(1);
numbers.add(2);
numbers.add(3);
print(numbers);//{1, 2, 3}
```

- Queue

```Dart
// Ordered, no index, add and remove from start and end

Queue items = new Queue();
items.add(1);
items.add(3);
items.add(2);
items.removeFirst();
items.removeLast();
print(items); // {3 }
```

- Map

```Dart
//Map = key value pair
Map people = {'dad': 'Bryan', 'son':'Chris'};
print(people); //{dad: Bryan, son: Chris};
print(people.keys); // (dad, son)
print(people.value); // (Bryan, Chris)
print(people['dad']); // Bryan

// Generic Type
Map<String, String> things = new Map<String, String>();
things.putIfAbsent('car', () => 'white');
print(things); // {car: white}
```
