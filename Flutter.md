### Debugging

- In VS Code > View > Appearance > Panel > DEBUG CONSOLE
- Debug Mode, adding break point
  - add to watch
- Flutter DevTools
  - Open DevTools in Web Browser

### Using Tunnel Pass Function between parent and child screen

#### Parent Class

1. create a button link to a function, which contains "showModalBottomSheet". It works as adding a stack of screen on the top of current screen
2. passing parent's "setState" function to child class, after child class pop the screen then it will call parent's builder function.

```Dart
  void _openOverlayScreen() {
    showModalBottomSheet(
        useSafeArea: true, //keep space for the device features
        isScrollControlled: true, // take full amount for height
        context: context,
        //call child class builder function, and pass parent function to child class
        builder: (cxt) => NewPlace(
              parentFunction: parentFunction,
            ));
  }
    void parentFunction(Place place) {
    setState(() {
      _myPlaces.add(place);
    });
  }
```

#### Child Class

1. child's constructor including parent's function
2. declare child's function including parent's function, and trigger by button

```Dart
  const NewPlace({super.key, required this.parentFunction});

  final void Function(Place place) parentFunction;

  void childFunction() {
    widget.parentFunction(
      //passing value into parent's function
      Place(
        id: 'hello',
        title: _enteredTitle,
      ),
    );
    //pop child's screen
    Navigator.pop(context);
  }

 OutlinedButton.icon(onPressed: childFunction)

```
