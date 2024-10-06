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
