### Part 4: Delete Data

1. In your `services/pets.dart`, create a function that returns future void, takes an argument of type `int` `petId`.

```dart
  Future<void> deletePet({required int petId}) async {}
```

2. Call your delete endpoint and pass the `petId` in the url.

```dart
  Future<void> deletePet({required int petId}) async {
    try {
      await _dio.delete(_baseUrl + '/pets/${petId}');
    } on DioError catch (error) {
      print(error);
    }
  }
```

3. In your Provider, create a function `deletePet` that takes an argument of type `int` `petId`.

```dart
  void deletePet(int petId) async {}
```

4. Call `PetsServices().deleteBook()` and pass it the `petId`.

```dart
  void deletePet(int petId) async {
    await DioClient().deletePet(petId: petId);
  }
```

5. Search for the pet with the same `id` and remove it from the list then call `notifyListeners`.

```dart
  void deletePet(int petId) async {
    await PetsServices().deletePet(petId: petId);
    pets.removeWhere((pet) => pet.id == petId);
    notifyListeners();
  }
```

6. In your `pet_card.dart` delete icon button, call this function and pass it the `pet.id`.

```dart
    IconButton(
        onPressed: () {
            Provider.of<PetsProvider>(context, listen: false).deletePet(pet.id!);
                        },
        icon: const Icon(
                Icons.delete,
                color: Colors.red,
        ))
```

### Part 5: Adopting A Pet.

1. In your `services/pets.dart`, create a function that returns future void, takes an argument of type `int` `petId`.

```dart
  Future<void> adoptPet({required int petId}) async {}
```

2. Call your adopt endpoint and pass the `petId` in the url.

```dart
  Future<void> adoptPet({required int petId}) async {
    try {
      Response response = await _dio.post(_baseUrl + '/pets/adopt/${petId}');
      retrievedPet = Pet.fromJson(response.data);
    } on DioError catch (error) {
      print(error);
    }
  }
```

3. In your Provider, create a function `adoptPet` that takes an argument of type `int` `petId`.

```dart
  void adoptPet(int petId) async {}
```

4. Call `PetsServices().adoptPet();` and pass it the `petId`.

```dart
  void adoptPet(int petId) async {
    await PetsServices().adoptPet(petId: petId);
  }
```

5. Search for the pet with the same `id` and change the `adopted` property to true and call `notifyListeners`.

```dart
  void adoptPet(int petId) async {
    await PetsServices().adoptPet(petId: petId);
    int index = pets.indexWhere((pet) => pet.id == newPet.id);
    pets[index].adopted = true;
    notifyListeners();
  }
```

6. In your `pet_card.dart` adopt button, call this function and pass it the `pet.id`.

```dart
ElevatedButton(
    onPressed: () {
            Provider.of<PetsProvider>(context, listen: false).adoptPet(pet.id!);
            },
    child: const Text("Adopt"),
),
```

7. Make the button disabled if the pet `adopted` property is `true`.

```dart
ElevatedButton(
    onPressed: pet.adopted
            ? null
            : () {
        Provider.of<PetsProvider>(context, listen: false).adoptPet(pet.id!);
                },
    child: const Text("Adopt"),
    ),
```
