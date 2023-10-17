# Meaning
## Definition
- poly(many) + morph(shape) + ism
- 다형성 : 같은 종의 생물이면서도 어떤 형태나 형질이 다양하게 나타나는 현상.

## 1. `is a`v.s. `has a` relationship
### Dog is an animal.

  

- `class Dog : public Animal`

- `class Dog` includes `class Animal` ’s every feature.

- The more derived class inherits, the more the class is specialized[구체화].

- A base class are generalized[일반화] than a derived class.

  

### Dog has a brain.

  

- `class Dog { private: Brain *brain; };`

- `class Dog` has a brain.

  

## 2. Overriding

  

```cpp

Animal animal = new Animal();

Dog dog = new Dog();

  

animal.makeSound(); // Animal's makeSound function calls

dog.makeSound(); // Dog's makeSound function calls

```

  

### Upcasting

  

```cpp

// Dog can be in a Animal pointer because dog is an animal.

Animal *animal2 = &dog; // Upcasting (Dog ->upto Animal)

animal2->makeSound(); // Basically Animal's makeSound function calls

```

  

### Downcasting

  

```cpp

Dog *dog2 = &animal; // Downcasting (Animal ->downto Dog)

```

  

- Downcasting causes compile error because animal has no attributes of dogs. (is undefined)

  

### Static Cast is dangerous

  

```cpp

// Runs normally

Animal *animal2 = &dog;

Dog *dog2 = static_cast<Dog *>(animal2); // animal2 is basically a dog.

dog2->makeSound(); // Dog's makeSound function calls.

  

// Causes Runtime Error

Dog *dog2 = static_cast<Dog *>(&animal); // animal is basically a animal.

dog2->makeSound(); // RUNTIME ERROR!

// Dog's makeSound function should be called,

// but there is no function, causes runtime error

```

  

### Use Dynamic Cast

  

```cpp

Dog *dog2 = dynamic_cast<Dog *>(&animal); // animal is basically a animal.

// causes Compile Error!

```

  

## 3. Virtual Keyword

  

### Dynamic Binding

  

- Function call is decided at runtime.

- Function addresses are in the virtual function table(vtable)

  

### Without Virtual Function

  

| class Animal | class Dog | object Animal | object Dog |

| --- | --- | --- | --- |

| Animal::makeSound(); | Dog::makeSound(); | string type; | |

  

```cpp

Animal *animal = new Dog();

  

animal->makeSound(); // Animal::makeSound();

```

  

### With Virtual Function

  

| object Animal | object Dog |
| --- | --- |
| vpointer→vtable | vpointer→vtable |
| string type; | |
| Virtual Function Table | Function Call | Address |


| --- | --- | --- |
| Animal | makeSound() | Animal::makeSound() |
| Dog | makeSound() | Dog::makeSound() |
  

### Pure Virtual Function

  

`virtual Func() = 0;`

  

### Abstract Class

  

- Has one or more pure virtual function.

- Can’t be instantiated.

  

## 4. Polymorphism

  

- dog can be a Dog and an Animal.

- Poly(many) + Morph (Shape) + ism