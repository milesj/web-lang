# Control Structures #

All control structures are curly brace based.

## if, elif, else ##

    STRUCTURE
        if STATEMENT {
        [ } elif STATEMENT { ]
        [ } else { ]
        }

    STATEMENT
        [ ( ] EXPRESSION [ ) ]

The most basic form of an `if` `else` block.

    if (foo) {
        // ...
    } else {
        // ...
    }
    
Else if blocks are also supported with `elif`.

    if (foo) {
        // ...
    } elif (bar) {
        // ...
    }
    
The parenthesis in expressions are also optional.

    if foo and bar {
        // ...
    }

## for ##

    STRUCTURE
        for STATEMENT in VARIABLE {
        [ } else { ]
        }

    STATEMENT
        VALUE |
        KEY, VALUE

    KEY, VALUE
        Uses variable naming conventions.

The `for` loop is used for iterating over collections, like arrays and maps.

    let foo = [1, 2, 3]
    
    for value in foo {
        // ...
    }
    
To access the key, separate with a comma.

    let bar = {1 => 'a', 2 => 'b', 3 => 'c'}
    
    for key, value in bar {
        // ...
    }
    
The `for` loop does not support the auto-incrementing form found in other languages, like C. 
However, we can create a new range and loop that instead.

    for i in Array.range(0, 10) {
        // 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
    }

The `break` statement will stop the loop.

    for value in foo {
        if (expression) {
            break
        }
    }

The `continue` statement will skip to the next item.

    for value in foo {
        if (expression) {
            continue
        }
    }
    
An `else` block can be defined that will execute if the collection is empty.

    for value in foo {
        // ...
    } else {
        // ...
    }

## loop ##

    STRUCTURE
        loop {
        }

The popular `while` and `do-while` loops are not supported, instead we have a simple `loop`. 
To exit the loop, call `break`.

    loop {
        // ...
        
        if (expression) {
            break
        }
    }

This is the same as writing `while (true)`.

## match ##

    STRUCTURE
        match VARIABLE {
            BLOCK
            [ BLOCK ]
            [ ... ]
        [ } else { ]
        }

    BLOCK
        STATEMENT {
        }

    STATEMENT
        [ ( ] EXPRESSION[, EXPRESSION[, ... ]] [ ) ]

The `match` block is similar to a switch case block, in that it executes different blocks based on a matching pattern.

    string var = 'foo'

    match (var) {
        ('foo') { // ... }
        ('bar') { // ... }
        ('baz') { // ... }
    }

This can be simplified by removing parenthesis.

    match var {
        'foo' { // ... }
        'bar' { // ... }
        'baz' { // ... }
    }

This is similar to writing this `if` block.

    if var == 'foo' {
        // ...
    } elif var == 'bar' {
        // ...
    } elif var == 'baz' {
        // ...
    }

Multiple patterns are separated with a comma.

    match var {
        'foo', 'bar' { // ... }
        'baz' { // ... }
    }

If no match is found, an `else` block can be defined.

    match var {
        // ...
    } else {
        // ...
    }

## try, catch, finally ##

    STRUCTURE
        try {
        } catch STATEMENT {
        [ } catch STATEMENT { ]
        [ ... ]
        [ } finally { ]
        }

    STATEMENT
        [ ( ] CLASS VARIABLE [ ) ]

These blocks are used for handling exceptions.

    try {
        // ...
    } catch (Exception e) {
        // ...
    }

The `finally` block is used for always executing code.

    try {
        // ...
    } catch (Exception e) {
        // ...
    } finally {
        // ...
    }

Multiple exceptions can also be caught.

    try {
        // ...
    } catch (FooException e) {
        // ...
    } catch (BarException e) {
        // ...
    }
