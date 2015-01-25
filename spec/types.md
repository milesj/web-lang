# Types #

All types are immutable objects that contain a value. If a type needs to be mutated, it will need to be unlocked or cloned.

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

    string foo = 'Hello'

## Compounds ##

Compound types are more complex types, like collections. The following compound types are supported.

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
            <td>list</td>
            <td>system.List</td>
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
They are created using brackets and should be assigned using `let`.

    let foo = [1, 2, 3]
    let bar = ['a', 'b', 'c']
    
To add an item to the end of an array.

    foo[] = 4
    
To add an item to the beginning.

    foo[^] = 0
    
To overwrite an item.

    foo[1] = 11
    
To access an item.

    let value = foo[0]
    
Since arrays are objects internally, they can also use methods.

    let first = foo.first()
    let last = foo.last()
    let bar = foo.filter().map()

### Tuples ###

Tuples are fixed length ordered lists of a specific type. Once created, they cannot be modified. 
They are created using parenthesis and should be assigned using `let`.

    let foo = (1, 2, 3)
    let bar = ('a', 'b', 'c')
    
To access an item.

    let value = bar[1] // b

