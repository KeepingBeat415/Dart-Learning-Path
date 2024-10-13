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

- Final Variable

```dart
//final variable can't reassign new value, but can call function for modify such as, using .shuffle()
final String text;
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

Using 'if' statements in Lists

````Dart
//No curly braces around the if statement
final myList = [1, 2, if (condition) 3];
final myList = [1, 2, if (condition) 3 else 4];

- Set

```Dart
// Set = unordered, not contain duplicates

Set<int> numbers = new Set<int>();
numbers.add(1);
numbers.add(2);
numbers.add(3);
print(numbers);//{1, 2, 3}
````

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

//ternary expressions
true ? 'this' : 'that';

//Spreading Values (...)
const numbers = [1, 2, 3];
const moreNums = [numbers, 4]; // [[1,2,3], 4]
const moreNums =[...numbers, 4] // [1, 2, 3, 4]
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

//Using "for" loops in lists
final numbers = [5, 6];
final myList = [
    1,
    2,
    //for...in syntax is a special variation of the for loop that loops through multiple items in a list
    for(final num in numbers)
        num
];
//Using "map"
final myList = [
    1,
    2,
    ...numbers.map((n){
        return n*2;
    })
];
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

### Imports

- Imports can be added as Package.
- List dependencies: Pubspec.yaml

```Dart
//Synchronous means one at a time.
//Asynchronous means many at once.

import 'package:http/http.dart' as http;

main(List<String> arguments){
    var url = "http://www.voidrealms.com";
    // Asynchronous
    http.get(url).then((response){
        print("Response status code: ${response.statusCode}");
    });
}
```

### Classes

```Dart
class Animal{

   //variable begin with '_' means privity class variable
   String _name = '';

   Animal(){
       print('Default constructor');
   }
   Animal(String name){
    _name = name;
   }

   void sayHello(){
       if(_name.isEmpty){
           print('Hello');
       }
       else{
           print('Hello ${_name} nice to meet you');
       }
   }
}
```

```Dart
import 'package:classes3/dog.dart';
main(List<String> arguments) {

  Dog bob = new Dog(6, 'Bob');

  print('${bob.name} is ${bob.ageInDogYears()} dog years old ');// 42 dog years old
}

class Dog {
  int age = 1;
  String name = 'fiddo';

  Dog(int age, String name) {
    this.age = age;
    this.name = name;
  }

  int ageInDogYears() => age * 7;
}
```

### Scope

```Dart

main(List<String> arguments){
    Animal cat = new Animal('fluffy', 16, 'Short Hair');
    //class public variable can re-assign out of class
    cat.breed = 'mixed';

    //class private variable cannot
    //cat._name = 'muffin'; => Error

    Animal dog = new Animal('Rango', 6);
    dog.name = 'fiddo';//setter
    print(dog.name);//getter

    //static function no instance, call directly
    Animal.run();

}

class Animal{
    //class scope
    String name = '';
    //class private variable begin with '_'
    int _age = 0;
    String breed = '';
    //static shared across all instances of the class
    static int _count = 0;

    Animal(String name, int age, String breed){
        //add this. point to class scope
        //for public variable, there's name collision, so we need to add "this."
        this.name = name;
        //private variable is able to assign directly
        _age = age;
        this.name = name;
        //every time constructor called, _counter +1
        _counter++;
    }

    //private function
    void _display(String message){
        print ('This is private function.');
    }
    //Getters and Setters function for access private variable
    String get name => _name;

    void set name(String value) => _name = value;

    //static doesn't have this. keyword
    static void run() {
        print('running');
    }
}
```

### Polymorphism

```Dart

import 'package:poly1/feline.dart';

main(List<String> arguments) {


  Feline cat = new Feline();

  cat.breath();// inheritance from Animal class

  cat.test();//override function

}

class Animal {

  bool isAlive = true;

  void breath() => print('breathing');

}

class Mamal extends Animal {

  bool hasHair = true;
  bool hasBackbone = true;
  bool isWarmBlooded = true;

  void walk() => print('Walking');

  void test() {
    print('testing in mamal');
    //super.test();
  }

}

import 'mamal.dart';

class Feline extends Mamal {

  bool hasClaws = true;

  void growl() => print('grrrrr');

  @override//override parent function
  void test() {
    print('testing in feline');
    super.test();//call parent class function using 'super.'
  }

}

class Dragon {
  bool breathsFire = true;

  void fly() => print('flying');


  void test() {
    print('Test called in Dragon');
  }
}

class Ghost {
  bool walksThoughWalls = true;

  void test() {
    print('Test called in Ghost');
  }
}

import 'feline.dart';
import 'dragon.dart';
import 'ghost.dart';

//Mixins --> multiple inheritance
class Monster extends Feline with Ghost, Dragon {

  bool glowInDark = true;

  @override
  void test() {
    print('Test called in Monster');
    super.test();//will randomly call one of extra extends parent function
  }
}
```

- Interfaces

```Dart

class Employee {

  String name = '';

  void test() => print('test');
}

//implements needs all getters, setters function
//when implement, need to implement specific in the Child class
class Manager implements Employee{
    //need to implements all variables and functions
    String name = 'Bob';

    void test () {
        print('I am a manager');
        //print(super.test()); cannot call parent's functions
        print(super.toString());//nothing print, and nothing inheritance
    }
}
```

### Abstraction

```Dart
//a class has property declarations without implementations
abstract class Car {
    bool hasWheels;
    bool hasHorn;

    //void honk();
    //abstract class can have concrete function
    void honk() => print('beep beep');
}

//Need filling out all not implement variables and functions
class RaceCar extends Car{
    RaceCar(){
        this.hasHorn = true;
        this.hasHorn = true;
    }
    void honk() {
        print('honk in racecar');
        super.honk();
}
```

### Generics

- generics

```Dart
//generics handle it and make as unknown type
List values = [1, 2, 3, 4, 5];

//class can handle a different type
List<int> numbers = new List<int>;
numbers.addAll([1,2,3,4]);

print(numbers);//[1, 2, 3, 4]

add(1, 2); //3
add<int>(1, 2); //3

//Simple Example
void add<T>(T a, T b){
    print(a + b);
}

//More complex
//extends make restrict for parameter type
void addNumbers<T extends num>(T a, T b){
    print(a + b);
}
//T >> arguments type
T add<T extends num>(T value, List<T> items){
    T ret = value;
    items.forEach(value){
        ret = ret + value;
    }
    return ret;
}
```

- Generic Class

```Dart
main(List<String> arguments){
    Counter<double> doubles = new Counter<double>();
    doubles.addAll([1.0,2.2,3.6]);
    doubles.total();

    Counter<int> ints = new Counter<int>();
    ints.addAll([1,2,3]);
    ints.total();
}

class Counter<T extends num>{
    List<T> _items = new List<T>();

    void addAll(Iterable<T> iterable) => _items.addAll(iterable);

    void add(T value) => _items.add(value);

    T elementAt(int index) => _items.elementAt(index);

    void total(){
        num ret = 0;
        items.forEach(value){
        ret = ret + value;
        }
        print(ret);
    }

}
```

### File System

- Sync vs Asynchronous
  - Synchronous means: things will happen one at a time.
    - For example: waiting on the queue for process
  - Asynchronous means: all things happen same time without wait.
    - For example: Student after school, and get out of school door

```Dart
import 'dart:io';

main(List<String> arguments){

    String path = '/';
    Directory dir = new Directory(path);

    if(dir.existsSync()){
        print('exists');
    }else{
        print('not found');
    }
    //open asynchronous, call Directory Static class and creating a temp synchronously
    Directory dir2 = Directory.systemTemp.createTempSync();

    print(dir2.path);

    if(dir2.existsSync()) {
        print('Removing ${dir2.path}');
        dir2.deleteSync();
    }
    else {
        print('Could not find ${dir2.path}');
    }

    Directory dir3 = Directory.current;
    print(dir.path);

    List<FileSystemEntity> list = dir.listSync(recursive: true);

    print('Entries in list: ${list.length}');

    FileStat stat = value.statSync();
    print('Path: ${ value.path}');
    print('Type: ${stat.type}');
    print('Changed: ${stat.changed}');
    print('Modified: ${stat.modified}');
    print('Accessed: ${stat.accessed}');
    print('Mode: ${stat.mode}');// denotes the system access you have to it
    print('Size: ${stat.size}');
    print('');

    File file = new File(dir.path + '/myfile.txt');

    writeFile(file);
    readFile(file);

}

void writeFile(File file){
    //Append, Write
    RandomAccessFile raf = file.openSync(mode: FileMode.APPEND);

    raf.writeStringSync('Hello World!\r\nHow are you today?');
    raf.flushSync();//flush buff data into file
    raf.closeSync();
}

void readFile(File file){
    if(!file.existsSync()){
        print('file not found!');
        return;
    }

    print('Reading string...');
    print(file.readAsStringSync());

    print('Reading bytes....');
    List values = file.readAsBytesSync();
    values.forEach((value) => print(value));
}

```
