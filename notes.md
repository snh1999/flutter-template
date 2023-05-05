```bash
lib/
|-- data/
| |-- repositories/ # (implementation of domain layer)
| |-- datasources/ # (fetch/ modify data, return model)
| |-- models/ # (extend entity, JSON-dart object)
| |-- exceptions/
|-- domain/ # (independent)
| |-- entities/ # (business objects)
| |-- repositories/ # (abstract class)
| |-- usecases/ # (core business logic)
|-- presentation/ # (handles basic input conversion and validation.)
| |-- screens/
| |-- state management/ # (delegates all its work to use cases).
| |-- widgets/
|-- utils/
|-- di/
| |-- app_module.dart
|-- main.dart
|-- app.dart
|-- theme.dart
|-- colors.dart
|-- constants.dart
```

add dependencies
start from independant layer - aka domain (after a rough rundown of UI design)
jump into entities (Nothing to test)

```dart
import 'package:equatable/equatable.dart';
class EntityName extends Equatable {
    // input properties here
    // constructor - initialize + call super([properties])
}
```

next up use cases
at least they will take data from repository and pass it to presentation layer

```dart
abstract class SomethingRepository {
  Future<Either<L, R>> getSomething(int number);
  Future<Either<L, R>> getRandom();
}
```

add a Error (inside core) features folder inside lib (Test files written using TDD always map to production files and append a "\_test" at the end of their name.)
we can use `mokito` to test without concrete implementation

```dart
class MockSomethingRepository extends Mock implements SomethingRepository {}

void main() {
  GetSomething usecase;
  MockSomethingRepository mockSomethingRepository;

  setUp(() {
    mockSomethingRepository = MockSomethingRepository();
    usecase = GetSomething(mockSomethingRepository);
  });



  test(
    'should do whatever you want',
    () async {
      // "On the fly" implementation of the Repository using the Mockito package.
      // When getConcreteNumberTrivia is called with any argument, always answer with
      // the Right "side" of Either containing a test yayayada_variable object.
      when(mockSomethingRepository.getSoomething(any))
          .thenAnswer((_) async => Right(yayayada_variable));
      // The "act" phase of the test. Call the not-yet-existent method.
      final result = await usecase.execute(number: yadayada_var);
      // UseCase should simply return whatever was returned from the Repository
      expect(result, Right(yayayada_variable));
      // Verify that the method has been called on the Repository
      verify((mockSomethingRepository.getSoomething(yayayada_variable)));
      // Only the above method should be called and nothing more.
      verifyNoMoreInteractions(mockSomethingRepository);
    },
  );
}
```

to avoid errors

```dart
class GetSomething {
  final SomethingRepository repository;

  GetSomething(this.repository);
  // implement functions
}
```
