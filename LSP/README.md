# LISKOV SUSTITUTION PRINCIPLE (Principio de sustitución Liskov)

> Sea q(x) una propiedad demostrable sobre objetos de x de tipo T. Entonces q(y) debería ser demostrable para objetos y de tipo S donde S es un subtipo de T.

Bueno… ehm… si alguien entendió lo que está arriba, que levante la mano…

En palabras más simples, el principio nos dice: si estás usando una clase y esta es extendida, debes de poder utilizar cualquier clase hija, y que la aplicación siga funcionando sin problemas, o mejor aún, que las pruebas del padre sigan siendo válidas.

# Ejercicio:

* Aplicar el principio de sustitución Liskov en el siguiente ejemplo de código:

```ts
interface UsersProvider {
    getUsers(): any[]; 

const users = [
    {
        name: 'John',
        lastname: 'Doe',
        email: 'example@gmail.com'
    }
];

class UsersMySQL implements UsersProvider {
    getUsers() {
        return users;
    }
}

class UsersMongo implements UsersProvider {
    getUsers() {
        return users;
    }
}

class UsersPostgreSQL implements UsersProvider {
    getUsers() {
        return users;
    }
}

function getUsers(usersProvider: UsersProvider) {
    return usersProvider.getUsers();
}

```

* Tu trabajo es lograr que la función getUsers pueda recibir cualquier clase que tenga un método getUsers, y que este devuelva un array de usuarios. Esto lo puedes lograr utilizando el principio de sustitución Liskov.