
⭐ [Introduction to Object Oriented Programming in JavaScript](https://www.geeksforgeeks.org/introduction-object-oriented-programming-javascript/) - GeeksForGeeks

⭐ [Object-Oriented Programming (OOP)](https://www.techtarget.com/searchapparchitecture/definition/object-oriented-programming-OOP) - TechTarget

⭐ [Object Oriented Design](https://www.geeksforgeeks.org/oops-object-oriented-design/) - GeeksForGeeks


# OOD vs OOP

OOD (Object-Oriented Design) and OOP (Object-Oriented Programming) are closely related concepts, though they represent different stages in the software development process:

- **Object-Oriented Design (OOD):** This is the **planning phase** that focuses on structuring your software using object-oriented principles. During OOD, you define the objects, their properties (data), behaviours (methods), and the relationships between them. It's like creating a blueprint for your code.

- **Object-Oriented Programming (OOP):** This is the **implementation phase** where you use a programming language like Java, Kotlin, or Swift to translate your OOD design into actual code. You create classes based on your design, write methods to define the object's behaviours, and establish relationships between objects. It's like building a house based on the blueprint.


# What is Object Oriented Programming (OOP)
**Object Oriented Programming (OOP)** is a programming paradigm based on the concept of objects, 

## Key Concepts of OOP

### Classes and Objects
- **Class**: A class is not a real world object but we can create objects from a class. Its like a blueprint for creating objects. It defines a datatype by bundling data and methods that work on the data.

We can create classes using the `class` keyword which is reserved keyword in JavaScript. Classes can have their own properties and methods.

- **Object**: An object is an instance of a class. It is created using the class blueprint and contains real values instead of variables.

```js
// Base class for library items
class LibraryItem {
  constructor(title, publicationDate) {
    this.title = title;
    this.publicationDate = publicationDate;
  }

  getDetails() {
    return `${this.title}, published on ${this.publicationDate}`;
  }
}

// Subclass for books
class Book extends LibraryItem {
  constructor(title, publicationDate, author) {
    super(title, publicationDate);  // Call the parent class constructor
    this.author = author;
  }

  getDetails() {
    return `${this.title} by ${this.author}, published on ${this.publicationDate}`;
  }
}

// Subclass for magazines
class Magazine extends LibraryItem {
  constructor(title, publicationDate, issueNumber) {
    super(title, publicationDate);  // Call the parent class constructor
    this.issueNumber = issueNumber;
  }

  getDetails() {
    return `${this.title}, Issue No: ${this.issueNumber}, published on ${this.publicationDate}`;
  }
}

// Class to manage library items
class Library {
  constructor() {
    this.items = [];
  }

  addItem(item) {
    this.items.push(item);
  }

  listItems() {
    return this.items.map(item => item.getDetails());
  }
}

// Creating objects (instances) of the classes
const book = new Book('1984', '1949-06-08', 'George Orwell');
const magazine = new Magazine('National Geographic', '2021-08-01', 202);

// Creating an object (instance) of the Library class and adding items to it
const library = new Library();
library.addItem(book);
library.addItem(magazine);

// Listing all items in the library
console.log(library.listItems());
// Output:
// [
//   '1984 by George Orwell, published on 1949-06-08',
//   'National Geographic, Issue No: 202, published on 2021-08-01'
// ]
```

### Four Pillars of OOP

#### 1. Encapsulation
- Encapsulation is the bundling of data (variables) and methods (functions) that operate on the data into a single unit or class.
- It restricts direct access to some of an object’s components, which can prevent the accidental modification of data.

```js
class Book {
  constructor(title, author, isbn) {
    this._title = title;  // Private properties
    this._author = author;
    this._isbn = isbn;
  }

  // Getter methods to access private properties
  getTitle() {
    return this._title;
  }

  getAuthor() {
    return this._author;
  }

  getIsbn() {
    return this._isbn;
  }

  // Setter methods to update private properties
  setTitle(title) {
    this._title = title;
  }

  setAuthor(author) {
    this._author = author;
  }

  setIsbn(isbn) {
    this._isbn = isbn;
  }
}

const book = new Book('1984', 'George Orwell', '1234567890');
console.log(book.getTitle());  // Output: 1984
book.setTitle('Animal Farm');
console.log(book.getTitle());  // Output: Animal Farm
```

#### 2. Inheritance
- Inheritance is a mechanism where a new class (child class) inherits properties and methods from an existing class (parent class).
- It promotes code reusability and establishes a natural hierarchy.

```js
class LibraryItem {
  constructor(title, publicationDate) {
    this.title = title;
    this.publicationDate = publicationDate;
  }

  getDetails() {
    return `${this.title}, published on ${this.publicationDate}`;
  }
}

class Book extends LibraryItem {
  constructor(title, publicationDate, author) {
    super(title, publicationDate);  // Call the parent class constructor
    this.author = author;
  }

  getDetails() {
    return `${this.title} by ${this.author}, published on ${this.publicationDate}`;
  }
}

const book = new Book('1984', '1949-06-08', 'George Orwell');
console.log(book.getDetails());  // Output: 1984 by George Orwell, published on 1949-06-08
```

#### 3. Polymorphism
- Polymorphism allows objects of different classes to be treated as objects of a common superclass.
- It is achieved through method overriding (where a subclass provides a specific implementation of a method already defined in its superclass) and method overloading (multiple methods with the same name but different parameters).

```js
class LibraryItem {
  constructor(title, publicationDate) {
    this.title = title;
    this.publicationDate = publicationDate;
  }

  getDetails() {
    return `${this.title}, published on ${this.publicationDate}`;
  }
}

class Book extends LibraryItem {
  constructor(title, publicationDate, author) {
    super(title, publicationDate);
    this.author = author;
  }

  getDetails() {
    return `${this.title} by ${this.author}, published on ${this.publicationDate}`;
  }
}

class Magazine extends LibraryItem {
  constructor(title, publicationDate, issueNumber) {
    super(title, publicationDate);
    this.issueNumber = issueNumber;
  }

  getDetails() {
    return `${this.title}, Issue No: ${this.issueNumber}, published on ${this.publicationDate}`;
  }
}

const items = [
  new Book('1984', '1949-06-08', 'George Orwell'),
  new Magazine('National Geographic', '2021-08-01', 202)
];

items.forEach(item => console.log(item.getDetails()));
// Output:
// 1984 by George Orwell, published on 1949-06-08
// National Geographic, Issue No: 202, published on 2021-08-01
```

#### 4. Abstraction
- Abstraction means hiding the complexity and showing only the essential features of the object.
- It helps in reducing programming complexity and effort.

```js
class Library {
  constructor() {
    this.items = [];
  }

  addItem(item) {
    this.items.push(item);
  }

  listItems() {
    return this.items.map(item => item.getDetails());
  }
}

const library = new Library();
library.addItem(new Book('1984', '1949-06-08', 'George Orwell'));
library.addItem(new Magazine('National Geographic', '2021-08-01', 202));

console.log(library.listItems());
// Output:
// [
//   '1984 by George Orwell, published on 1949-06-08',
//   'National Geographic, Issue No: 202, published on 2021-08-01'
// ]
```
