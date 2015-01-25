# Types #

All types are immutable objects that contain a value. All mutations and aggregations will return a new instance with the
new value. If a type needs to be mutated in place, it will need to be unlocked or cloned.

## Primitives ##

The following basic types are supported, coupled with their alias and class.

<table>
    <thead>
        <tr>
            <td>Type</td>
            <td>Class</td>
            <td>Description</td>
            <td>Range</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>object</td>
            <td>system.Object</td>
            <td>Base type that all types extend from.</td>
            <td></td>
        </tr>
        <tr>
            <td>null</td>
            <td>system.Null</td>
            <td>Absence of value.</td>
            <td></td>
        </tr>
        <tr>
            <td>bool</td>
            <td>system.Boolean</td>
            <td>A true or false.</td>
            <td></td>
        </tr>
        <tr>
            <td>byte</td>
            <td>system.Int8</td>
            <td>8-bit signed integer.</td>
            <td>-128 to 127</td>
        </tr>
        <tr>
            <td>ubyte</td>
            <td>system.UInt8</td>
            <td>8-bit unsigned integer.</td>
            <td>0 to 255</td>
        </tr>
        <tr>
            <td>short</td>
            <td>system.Int16</td>
            <td>16-bit signed integer.</td>
            <td>-32,768 to 32,767</td>
        </tr>
        <tr>
            <td>ushort</td>
            <td>system.UInt16</td>
            <td>16-bit unsigned integer.</td>
            <td>0 to 65,535</td>
        </tr>
        <tr>
            <td>int</td>
            <td>system.Int32</td>
            <td>32-bit signed integer.</td>
            <td>-2,147,483,648 to 2,147,483,647</td>
        </tr>
        <tr>
            <td>uint</td>
            <td>system.UInt32</td>
            <td>32-bit unsigned integer.</td>
            <td>0 to 4,294,967,295</td>
        </tr>
        <tr>
            <td>long</td>
            <td>system.Int64</td>
            <td>64-bit signed integer.</td>
            <td>–9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</td>
        </tr>
        <tr>
            <td>ulong</td>
            <td>system.UInt64</td>
            <td>64-bit unsigned integer.</td>
            <td>0 to 18,446,744,073,709,551,615</td>
        </tr>
        <tr>
            <td>float</td>
            <td>system.Single</td>
            <td>32-bit floating-point.</td>
            <td>???</td>
        </tr>
        <tr>
            <td>double</td>
            <td>system.Double</td>
            <td>64-bit floating-point.</td>
            <td>???</td>
        </tr>
        <tr>
            <td>string</td>
            <td>system.String</td>
            <td>Sequence of Unicode characters.</td>
            <td></td>
        </tr>
    </tbody>
</table>

### Booleans ###

Booleans represent either a `true` or `false` value.

    bool foo = true
    
### Integers ###

Integers are whole numbers that support either signed (negatives) or unsigned values (non-negatives). 
They are represented as 4 different types -- `byte`, `short`, `int`, and `long` -- each with their own fixed length.

    byte foo = 127
    ushort bar = 65535

### Floating Points ###

Floating points are approximated numbers that have radix points that are of a variable size. 
They are represented as 2 different types -- `float` and `double`.

    float foo = 123.45

### Strings ###

Strings are a sequence of zero or more Unicode characters that are initialized using single quotes. 
They are valid UTF-8 encoded sequences.

    string foo = 'Hello'

Double quote strings can be used for interpolation as well as internal expressions.

    string foo = 'World'
    string bar = "Hello {foo}"
    string baz = "1 + 2 is {1 + 2}"
    
    bar // Hello World
    baz // 1 + 2 is 3

## Compounds ##

Compound types are more complex types, like collections. When declared, they either need to use [generics](generics.md), 
or use [type inference](#inference) via the `let` keyword.

The following compound types are supported.

<table>
    <thead>
        <tr>
            <td>Type</td>
            <td>Class</td>
            <td>Description</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>array</td>
            <td>system.Array</td>
            <td>A variable length index based list.</td>
        </tr>
        <tr>
            <td>tuple</td>
            <td>system.Tuple</td>
            <td>A fixed length ordered list.</td>
        </tr>
        <tr>
            <td>map</td>
            <td>system.Map</td>
            <td>A variable length key-value map.</td>
        </tr>
        <tr>
            <td>struct</td>
            <td>system.Struct</td>
            <td>A fixed length key-value map.</td>
        </tr>
        <tr>
            <td>enum</td>
            <td>system.Enum</td>
            <td>A set of constant values.</td>
        </tr>
    </tbody>
</table>

### Arrays ###

Arrays are variable length lists of a specific type, with indices represented as 0-based integers.

    Array<int> foo = [1, 2, 3]
    Array<string> bar = ['a', 'b', 'c']
    
Using arrays is pretty similar to other languages. You can add an item.

    foo[] = 4

Or access an item by index. If the index doesn't exist, an exception is thrown.

    foo[0] // 1

If an array is mutable, you can overwrite an item by index.

    foo[0] = 123

A range of values (slices) can also be retrieved.

    foo[1:3]
    foo[-1]

### Tuples ###

Tuples are immutable fixed length ordered lists of a specific type. Once created, they cannot be modified.

    Tuple<byte> foo = (1, 2, 3)
    Tuple<string> bar = ('a', 'b', 'c')

Tuples only support accessing items.

    bar[1] // b

### Maps ###

Maps are key-value based sets, with the key being one type, and the value being another.
All types are usable as keys, excluding booleans.

    Map<string, int> foo = {'a': 1, 'b': 2}

Adding and setting a value on the map is the same. Uses dot notation.
If they key is dynamic, or not alpha-numeric, use brackets.

    foo.c = 3
    foo[var] = 3

Accessing a value uses the same notation.

    foo.a // 1
    foo[var]

### Structs ###

Structs are key-value based sets where the field names are always constant and always required.
When defining a struct, the field must by typed.

    struct Point {
        x: int,
        y: int
    }
    
    Point foo = Point {x: 123, y: 456}

The fields on the struct can then be accessed and set using dot notation.

    foo.x = 789
    foo.x // 789

### Enums ###

Enums are a set of identifiers that are always constant once declared. Identifiers are implicitly integer 0-based.

    enum Color {
        RED,
        GREEN,
        BLUE
    }
    
    Color foo = Color.RED

Values can be access using dot notation.

    Color.GREEN // 1

Enums are very handy in comparisons.

    if foo == Color.RED {
        // ...
    }

## Inference ##

Type inference is a concept where a variables type will be automatically deduced when the type is omitted 
from the declaration. To use type inference, use the `let` keyword.

    let foo = 123
    let bar = {1: 'a', 2: 'b'}

The previous example is equivalent to this explicit declaration.

    byte foo = 123
    Map<byte, string> bar = {1: 'a', 2: 'b'}

## Mutability ##

By default, all types are immutable when declared. If any mutation occurs, an exception is thrown. 
There are 3 options for mutability. 

    string foo = 'Hello'
    foo += ' World' // INVALID

The first option is to clone the value using the `clone()` method. 
This approach will only work if used in the declaration, as the string is still being initialized.

    string bar = foo.clone() + ' World' // VALID

The second option is to unlock the object, which makes it mutable.

    foo.unlock()
    foo += ' World' // VALID

The third option is to mark the variable as mutable during declaration, by append `!` to the type.

    string! foo = 'Hello'
    foo += ' World' // VALID

The `!` can be used with any type, even the `let` keyword. Take the following examples.

    let! foo = 'Hello world'
    short! bar = -32,768
    Array<int>! baz = [1, 2, 3]

## Nullable ##

All types are non-nullable by default.

    int foo = 123
    foo = null // INVALID

To make a type nullable, append `?` to the type.

    int? foo = 123
    foo = null // VALID

Nullable can also be paired with mutable. The order of characters don't matter.

    int!? foo = 123
    int?! foo = 456

## Conversion ##

Both implicit (expressions, etc) and explicit type conversion is supported. To manually convert a type to another,
prepend the variable with parenthesis of the new type.

    float x = 2.5
    (int) x // 3

Automatic conversion also happens when a variable of one type is assigned to another variable of another type. 
This is also known as boxing.

    float x = 2.5
    int y = x // 3

## Augmenting ##

Augmenting is a concept that allows the extending of built-in type classes at runtime,
like adding new methods.

The following example uses [package](packages.md) and [class](classes.md) syntax.

    import system.String
    
    augment String {
        string wrap(string name) {
            return "<{name}>" + this + "</{name}>"
        }
    }
    
    'Hello world'.wrap('div') // <div>Hello world</div>
