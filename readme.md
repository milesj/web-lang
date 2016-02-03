This specification is for a programming language designed for the web, specifically HTTP, that runs on both the frontend and backend. The language aims to be object oriented through classes, interfaces, and traits, strongly typed with static-type checking at compile time, memory safe coupled with immutable only data structures and types, and much more.

The following specifications are proof of concept, which mainly define the syntax and some functionality. It is not an actual usable programming language. Simply thoughts in my head.

* [Basics](spec/basics.md)
    * [Identifiers](spec/basics.md#identifiers)
    * [Keywords](spec/basics.md#keywords)
    * [Literals](spec/basics.md#literals)
    * [Variables](spec/basics.md#variables)
    * [Constants](spec/basics.md#constants)
    * [Expressions](spec/basics.md#expressions)
* [Types](spec/types.md)
    * [Primitives](spec/types.md#primitives)
        * [Boolean](spec/types.md#boolean)
        * [Integers](spec/types.md#integers)
        * [Floating Points](spec/types.md#floating-points)
        * [Strings](spec/types.md#strings)
            * [Interpolation](spec/types.md#interpolation)
            * [Concatenation](spec/types.md#concatenation)
    * [Collections](spec/types.md#collections)
        * [Arrays](spec/types.md#arrays)
        * [Tuples](spec/types.md#tuples)
        * [Maps](spec/types.md#maps)
        * [Structs](spec/types.md#structs)
        * [Enums](spec/types.md#enums)
    * [Annotations](spec/types.md#annotations)
    * [Conversion](spec/types.md#conversion)
* Operators
    * Ternary
* [Control Structures](spec/control-structures.md)
    * [if, elif, else](spec/control-structures.md#if-elif-else)
    * [for](spec/control-structures.md#for)
    * [loop](spec/control-structures.md#loop)
    * [match](spec/control-structures.md#match)
    * [try, catch, finally](spec/control-structures.md#try-catch-finally)
* Exceptions
* Classes
    * Properties
    * Constants
    * Methods
    * Constructors
    * Destructors
    * Modifiers
    * Visibility
    * Inheritance
    * Overloading
    * Getters & Setters
* Interfaces
* Traits
* Generics
    * Covariance & Contravariance
* Packages
    * Importing
    * Package Managers
* Iterators
* Lambdas
* Asynchronous
* Threading
* Events
