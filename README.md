# Pets Adoption App 🦄

- Endpoints:

```
Get pets, type: Get, https://coded-pets-api-crud.herokuapp.com/pets
Create a new pet, type: Post, https://coded-pets-api-crud.herokuapp.com/pets
Update a pet, type: Put, https://coded-pets-api-crud.herokuapp.com/pets/{petId}
Delete a pet, type: Delete, https://coded-pets-api-crud.herokuapp.com/pets/{petId}
Adopt a pet, type: Post, https://coded-pets-api-crud.herokuapp.com/pets/adopt/{petId}
```

### Part 4: Delete Data

1. In your `services/pets.dart`, create a function that returns future void, takes an argument of type `int` `petId`.
2. Call your delete endpoint and pass the `petId` in the url.
3. In your Provider, create a function `deletePet` that takes an argument of type `int` `petId`.
4. Call `PetsServices().deleteBook()` and pass it the `petId`.
5. Search for the pet with the same `id` and remove it from the list then call `notifyListeners`.
6. In your `pet_card.dart` delete icon button, call this function and pass it the `pet.id`.

### Part 5: Adopting A Pet.

1. In your `services/pets.dart`, create a function that returns future void, takes an argument of type `int` `petId`.
2. Call your adopt endpoint and pass the `petId` in the url.
3. In your Provider, create a function `adoptPet` that takes an argument of type `int` `petId`.
4. Call `PetsServices().adoptPet();` and pass it the `petId`.
5. Search for the pet with the same `id` and change the `adopted` property to true and call `notifyListeners`.
6. In your `pet_card.dart` adopt button, call this function and pass it the `pet.id`.
7. Make the button disabled if the pet `adopted` property is `true`.
