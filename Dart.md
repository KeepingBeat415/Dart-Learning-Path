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

### Flow Control

- Assert

```Dart
int age = 43;
assert(age == 43);// checking true/false
assert(age == 15);// unhandled exception: Failed assertion: 'age == 15':is not true

```

- IF ELSE

```Dart

int age = 43;
if(age == 43) print ('You are 43 years old');
if(age != 43) print ('You are not 43 years old'); // ! =

if(age == 43) {
    print ('You are 43 years old');
} else {
    print ('You are not 43 years old')
};
```

- Scope

```Dart
// Scope: variable visibility ==>> same concept as global variable/class variable/privity variable
int age = 43;

if(age == 43) {
    //Failed, unhandled exception: NoSuchMethodError: No top-level getter 'hasBills' declared
    print ('You are 43 years old and has bills ${hasBills}');
} else {
    bool hasBills = true;
    print ('You are not 43 years old and has bills ${hasBills}')
};
```

- Switch

```Dart
int age = 18;

switch(age){

    case 18:
        print ('You are 18 years old');
        break;
    case 21:
        print ('You are 18 years old');
        break;
    default:
        print ('Nothing special about this age');
        break;
}

```

- Loops

```Dart
int value;
int init = 1;
int max = 5;

value = init;

//Run at least one time
do {
    print(value);
    value++;
} while (value < max);

//
while (value <= max){
    print(value);
    value++;
}

//Infinite loop
value = init;
do{
    if(value == 3){
        print('Value is 3');
        continue;
    }
    if(value > 5){
        print('Value is greater then 5');
        break;
    }
}while(true);
```

- For Each

```Dart
List people = ['Bryan', 'Heather', 'chris'];

for(int i = 0; i < people.length; i++){
    print('Person at ${i} is ${people[i]}');
}
// anonymous function
people.forEach((String person) {
    print(person);
});
```

### Functions

- Basic Functions

```Dart
main(List<String> arguments){
    sayHello('Bryan');

    print('Your age in dog years is ${dogYears(43)}');
}

void sayHello(String name){
    print('Hello ${name}');
}

int dogYears(int age){
    return age * 7;
}

```

- Optional Parameters

```Dart
main(List<String> arguments){
    sayHello('Bryan');
}
// Parameters with bracket means optional parameters
void sayHello([String name = '']){
    if(name.isNotEmpty) name = name.padLeft(name.length + 1);
    print('Hello ${name}');
}
```

- Name Parameters

```Dart

main(List<String> arguments){
    int footage = squartFeet(length: 10, width: 5);

    download('myfile'); // Download myfile on port 80
    download('myfile', port: 90);// Download myfile on port 90
}
// Parameters assign value by name
void squartFeet({int width, int length}){
    return width * length;
}

// Optional parameters assign value by name
void download(String file, {int port: 80}){
    print('Download ${file} on port ${port}');
}
```

- Functions as objects

```Dart
main(List<String> arguments){
    var dogyears = calcYears;

    print('Your age in dog years is ${dogyear(age: 43, multiplier: 7)}');
}

int calcYears({int age, int multiplier}){
    return age * multiplier;
}

```

- Anonymous Functions

```Dart

List people = ['Bryan', 'Heather', 'chris'];

// .where with anonymous function creates a new list and filter by switch case
people.where((String name) {
    switch(name){
        case 'Chris':
            return true;
        case 'Bryan':
            return false;
        case 'Heather':
            return true;
    }
}).forEach(print);// Heather chris
```

### Error Handling

- Exceptions

```Dart
//Error is a program failure
//Exception - can be handled

int age;
int dogyears = 7;

try{
    int age;
    int dogyears = 7;
    print(age * dogears);
}cath(e){
    print('There was an error: ${e.toString()}');
}finally{
    print('complete');
}

```

```Dart


main(List<String> arguments) {

  try {
    int age;
    int dogYears = 8;

    if(dogYears != 7) throw new Exception('dog years must be 7');
    // catch by "catch(e)", and exception message passed into catch block

    if(age == null) throw new NullThrownError();

    print(age * dogYears);
  }
  on NullThrownError {
    print('The value was null!!!');
  }
  on NoSuchMethodError {
    print('Sorry no such method');
  }
  catch (e) {
    print('Unknown error: ${e.toString()}');
  }
  finally {
    print('complete');
  }

}
```
