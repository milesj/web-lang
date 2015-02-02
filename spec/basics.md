# Basics #

## Identifiers ##

## Keywords ##

## Literals ##

## Variables ##

    DECLARATION
        TYPE VARIABLE[ MODIFIER ] = VALUE

    TYPE
        let | PRIMITIVE_TYPE | COLLECTION_TYPE

    PRIMITIVE_TYPE
        bool | [u]byte | [u]short | [u]int | [u]long | float | double | string

    COLLECTION_TYPE
        CLASS | CLASS<T> | CLASS<Tk, Tv>

    VARIABLE
        Name of the variable.

    MODIFIER
        ! | ?

    VALUE
        Value assigned to the variable. Should match TYPE declaration.

A variable is a named re-usable value that's associated with a specific type.

When declaring [primitive types](types.md#primitives), only the type alias should be used, instead of the class name.

    ushort foo = 123 // VALID, uses alias
    UInt16 foo = 123 // INVALID, uses class name

When declaring [collection types](types.md#collections), an inner generic type is required, unless the collection
does not require one.

    Array<int> foo = [1, 2, 3]
    Map<int, string> bar = {0: 'a', 1: 'b', 2: 'c'}
    Color baz = Color.RED // enumerable

Variable names can only contain alpha-numeric characters and underscores -- however,
it cannot start with a number. Variable names are also case sensitive and support Unicode.

    string foo_bar = '' // VALID
    string FooBar123 = '' // VALID
    string _fooBar = '' // VALID
    string 123foo = '' // INVALID
    string foo-BAR = '' // INVALID

[Mutable](types.md#mutable-modifier) and [nullable](types.md#nullable-modifier) modifiers are represented by `!` and `?`,
and are declared after the type.

    string foo?! = ''

## Constants ##

    DECLARATION
        const TYPE VARIABLE = VALUE

A constant is a variable that cannot be modified once declared. The constant name must be in all capitals.

    const int FOO = 123
    const string BAR = 'abc'
    const Map<int, string> BAZ = {}

The `let` keyword can be used in place of the type for implicit [type inference](types.md#type-inference).

    const let FOO = 123.45

Constants can also be used within [classes](classes.md#constants).

## Expressions ##
