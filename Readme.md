## Usage

if your project has flavors declared below :
```
productFlavors {
  apple {
    dimension fruit
  }
  orange {
    dimension fruit
  }
  banana {
    dimension fruit
  }
}
```
when you apply complex-dependency plugin, you need create a json file like :
```
"artifacts": [
  {
    "groupId": "com.google.code.gson"
    "artifactId": "gson"
    "version": "2.8.9"
    "flavors": [
      {
        "name": "apple",
        "version": "2.6.2"
      },
      {
        "name": "banana",
        "version": "2.8.9"
      }
  }
  ...
]
```
and you can depend different version with one third aar like ：
```
embedImplementation("com.google.code.gson:gson") { // if you do not declared a version, it will use the json's version that you expect
  embed "apple", "banana" // which will implementation on these flavors, orange will not depend the gson aar.
}
```
or
```
elimImplementation("com.google.code.gson:gson") {
  eliminate "apple", "banana" // which will NOT implementation on these flavors, orange will depend the gson aar.
}
```
