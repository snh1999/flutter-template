lib/
|-- data/
| |-- repositories/ (implementation of domain layer)
| |-- datasources/ (fetch/ modify data, return model)
| |-- models/ (extend entity, JSON-dart object)
| |-- exceptions/
|-- domain/ (independent)
| |-- entities/ (business objects)
| |-- repositories/ (abstract class)
| |-- usecases/ (core business logic)
|-- presentation/ (handles basic input conversion and validation.)  
| |-- screens/
| |-- state management/ (delegates all its work to use cases).
| |-- widgets/
|-- utils/
|-- di/
| |-- app_module.dart
|-- main.dart
|-- app.dart
|-- theme.dart
|-- colors.dart
|-- constants.dart
