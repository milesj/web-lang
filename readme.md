This specification is for a programming language designed for the web, specifically HTTP. The language aims to be 
object oriented, immutable, strongly typed, memory safe, garbage collected, statically typed via JIT or AOT compilation, 
and much more. 

The following specifications are proof of concept, and mainly define the syntax and some functionality. 
It is not an actual usable programming language. Simply thoughts in my head.

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
    * [Collections](spec/types.md#collections)
        * [Arrays](spec/types.md#arrays)
        * [Tuples](spec/types.md#tuples)
        * [Maps](spec/types.md#maps)
        * [Structs](spec/types.md#structs)
        * [Enums](spec/types.md#enums)
    * [Type Inference](spec/types.md#type-inference)
    * [Mutable Modifier](spec/types.md#mutable-modifier)
    * [Nullable Modifier](spec/types.md#nullable-modifier)
    * [Conversion](spec/types.md#conversion)
    * [Augmenting](spec/types.md#augmenting)
* Operators
    * Ternary 
    * Null Coalesce
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
