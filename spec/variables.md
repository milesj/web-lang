# Variables #

A variable is a named piece of data with a type and a value. Variables are declared using the assignment operator (`=`).

    foo = 123

### Syntax ###

    DECLARATION
        VARIABLE[TYPE] = PRIMITIVE_VALUE | COLLECTION_VALUE | BLOCK_VALUE
        VARIABLE[TYPE], VARIABLE[TYPE], ... = COLLECTION_VALUE | BLOCK_VALUE
        VARIABLE[TYPE], VARIABLE[TYPE], ... = PRIMITIVE_VALUE, PRIMITIVE_VALUE, ...

    VARIABLE
        Name of the variable.

    TYPE
        <PRIMITIVE_TYPE | COLLECTION_TYPE>

    PRIMITIVE_TYPE
        bool | [u]byte | [u]short | [u]int | [u]long | float | double | string

    COLLECTION_TYPE
        CLASS | CLASS<T> | CLASS<Tk, Tv>

    PRIMITIVE_VALUE
        Refer to primitive types specification.

    COLLECTION_VALUE
        Refer to collection types specification.

    BLOCK_VALUE
        Refer to block control structures specification.

### Semantics ###

* Cannot be defined without a value; will error otherwise.
* Naming conventions follow this pattern: `[a-z_]{1}[a-zA-Z0-9_]+`

## Explicit Typing ##

By default, variables use type inference, which deduce the type by analyzing the value. To mitigate this overhead, types can be explicitly defined using [generics](generics.md) like syntax.

    foo<byte> = 100
    bar<float> = 1252.42
    baz<string> = 'Hello World'
    qux<Array<int>> = [1, 2, 3]

This is primarily useful for collections.

## Multiple Assignment ##

Multiple variables can be declared in a single line by separating the variable names and values with commas.

    foo, bar = 123, 'Hello'
    foo<byte>, bar<string> = 123, 'Hello'

## Block Assignment ##

Variables can logically assign a value by evaluating a block. Blocks are represented by open `{` and close `}` curly brackets, in which encapsulated code will be evaluated and assigned using `yield`.

    foo = {
        if obj.status == 1
            yield 'ACTIVE'
        else
            yield 'PENDING'
    }

## Scoping ##

Variables are locally scoped to the contextual block in which they were declared.

    if true
        foo = 123

    {
        bar = "Hello"
    }

    foo // Undefined
    bar // Undefined

## Destructuring ##

Destructuring works in a similar fashion to multiple assignment, but uses the values within a [collection](types.md#collections) to assign from.

When assigning with arrays, tuples, or enums, the indices within the collection determine the variable order to assign to (from left to right, lowest to highest).

    foo, bar, baz = [1, 2, 3]

    foo // 1
    baz // 3

When assigning with maps or structs, the keys within the collection of the same name will determine the value to assign. This will only work with string keys.

    foo, baz = { 'foo': 1, 'bar': 2, 'baz': 3 }

    foo // 1
    baz // 3
