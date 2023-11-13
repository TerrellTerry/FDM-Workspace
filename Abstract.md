## Abstract Classes
- Classes are sometimes called blueprints for makig objects. Abstract classes are blueprints for making class definitions within a given hierarchy.
- Abstract classes are good for creating behaviors and attributes without making instantiable objects.

## Abstract Methods
- Abstract methods are method signatures without method bodies.
- This is useful to force any children to have an implementation for a mthod without defining a base implementation.

## Vertical Constructor Chaining
- The first line in any constructor must be a call to super() or a call to a constructor in the same class using this().
- Whenever you are making a constructor in a child class, you must first make a call to a constructor in a parent class.
- This can be used to ensure that any mandatory dependencies required by the parent class are met when making an instance of a child class.

## Horizontal Constructor Chaining
- Horizontal constructor chaining is a way to reuse a constructor in the same class.
- You can write logic in one constructor, and any overloaded constructors can resuse that logic by using the this() keyowrd syntax.

## Polymorphism
- Overloading (Early-binding or compile-time polymorphism)
    - Creating multiple method with the same method signature, but accepting in different arguments. This is used to give your user multiple ways to perform a given task based on available input.
- Overriding (late-binding or runtime polymorphism)
    - Giving a more specific implementation of a method defined in your parent class.   