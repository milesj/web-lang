# Types #

All types are immutable data structures that contain a value(s). Types can either be defined explicitly using generics, or implicitly through deference (default).

Furthermore, all types (and variables) are strictly immutable. Any "mutation" returns a new instance with the value being cloned and modified in the process.

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
            <td>sys.Object</td>
            <td>Base type that all types extend from.</td>
            <td></td>
        </tr>
        <tr>
            <td>bool</td>
            <td>sys.Boolean</td>
            <td>A true or false.</td>
            <td></td>
        </tr>
        <tr>
            <td>byte</td>
            <td>sys.Int8</td>
            <td>8-bit signed integer.</td>
            <td>-128 to 127</td>
        </tr>
        <tr>
            <td>ubyte</td>
            <td>sys.UInt8</td>
            <td>8-bit unsigned integer.</td>
            <td>0 to 255</td>
        </tr>
        <tr>
            <td>short</td>
            <td>sys.Int16</td>
            <td>16-bit signed integer.</td>
            <td>-32,768 to 32,767</td>
        </tr>
        <tr>
            <td>ushort</td>
            <td>sys.UInt16</td>
            <td>16-bit unsigned integer.</td>
            <td>0 to 65,535</td>
        </tr>
        <tr>
            <td>int</td>
            <td>sys.Int32</td>
            <td>32-bit signed integer.</td>
            <td>-2,147,483,648 to 2,147,483,647</td>
        </tr>
        <tr>
            <td>uint</td>
            <td>sys.UInt32</td>
            <td>32-bit unsigned integer.</td>
            <td>0 to 4,294,967,295</td>
        </tr>
        <tr>
            <td>long</td>
            <td>sys.Int64</td>
            <td>64-bit signed integer.</td>
            <td>–9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</td>
        </tr>
        <tr>
            <td>ulong</td>
            <td>sys.UInt64</td>
            <td>64-bit unsigned integer.</td>
            <td>0 to 18,446,744,073,709,551,615</td>
        </tr>
        <tr>
            <td>float</td>
            <td>sys.Single</td>
            <td>32-bit floating-point.</td>
            <td>???</td>
        </tr>
        <tr>
            <td>double</td>
            <td>sys.Double</td>
            <td>64-bit floating-point.</td>
            <td>???</td>
        </tr>
        <tr>
            <td>string</td>
            <td>sys.String</td>
            <td>Sequence of Unicode characters.</td>
            <td></td>
        </tr>
    </tbody>
</table>

### Booleans ###

Booleans represent either a `true` or `false` value.

    foo = true

### Integers ###

Integers are whole numbers that support either signed (negatives) or unsigned values (non-negatives). They are represented as 4 different types -- `byte`, `short`, `int`, and `long` -- each with their own fixed length.

    foo = 127
    bar = 65535

### Floating Points ###

Floating points are approximated numbers that have radix points of a variable size. They are represented as 2 different types -- `float` and `double`.

    foo = 123.45

### Strings ###

Strings are a sequence of zero or more Unicode characters that are initialized using single or double quotes. They are valid UTF-8 encoded sequences.

    foo = 'Hello'

#### Interpolation ####

    foo = 'World'
    bar = "Hello #{foo}"
    baz = "1 + 2 is #{1 + 2}"

#### Concatenation ####

    foo = "Hello" + " World"

## Collections ##

Collections are complex types that manage a set of types. The following collection types are supported.

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
            <td>sys.Array</td>
            <td>A variable length list.</td>
        </tr>
        <tr>
            <td>tuple</td>
            <td>sys.Tuple</td>
            <td>A fixed length list.</td>
        </tr>
        <tr>
            <td>map</td>
            <td>sys.Map</td>
            <td>A variable length key-value map.</td>
        </tr>
        <tr>
            <td>struct</td>
            <td>sys.Struct</td>
            <td>A fixed length key-value map.</td>
        </tr>
        <tr>
            <td>enum</td>
            <td>sys.Enum</td>
            <td>A set of constant values.</td>
        </tr>
    </tbody>
</table>

### Arrays ###

Arrays are variable length lists of a specific type, with indices represented as 0-based integers.

    foo = [1, 2, 3]
    bar = ['a', 'b', 'c']

### Tuples ###

Tuples are fixed length ordered lists of a specific type. Once created, they cannot be modified.

    foo = (1, 2, 3)
    bar = ('a', 'b', 'c')

### Maps ###

Maps are key-value based sets, with the key being one type, and the value being another. All types are usable as keys, excluding booleans.

    foo = { 'a': 1, 'b': 2 }

### Structs ###

Structs are key-value based sets where the field names are always constant and always required. When defining a struct, the field must by typed.

    struct Point {
        'x': int,
        'y': int
    }

    foo = Point { 'x': 123, 'y': 456 }

### Enums ###

Enums are a set of identifiers that are always constant once declared. Identifiers are implicitly integer 0-based.

    enum Color {
        RED,
        GREEN,
        BLUE
    }

    foo = Color.RED

## Annotations ##

By default, all variable types are inferred upon declaration. To define explicit types, we can use type annotations, which use [generics](generics.md) styled syntax.

    foo<byte> = 100
    bar<float> = 1252.42
    baz<string> = "Hello World"
    qux<Array<int>> = [1, 2, 3]

## Conversion ##

Both implicit (expressions, etc) and explicit type conversion is supported. To manually convert a type to another, prepend the variable with parenthesis of the new type.

    x = 2.5
    y = (int) x // 3

Automatic conversion also happens when a variable of one type is assigned to another variable of another type. This is also known as boxing.

    x = 2.5
    y<int> = x // 3
