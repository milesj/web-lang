# Control Structures #

Control structures are derived from C styled syntax and make use of curly braces.

## Conditional ##

The flow of execution is handled by conditional branches (or blocks) through the evaluation of expressions.

### Syntax ###

    STRUCTURE
        if EXPRESSION {
        [ } elif EXPRESSION { ]
        [ } else { ]
        }

    EXPRESSION
        Refer to the expressions specification.

### If-Then Statement ###

The most basic form is an `if` conditional block. If the expression evaluates to true, then the statement (body of the block) will be executed.

    if foo {
        // ...
    }

### Else-If-Then Statement ###

Branching is made possible through `elif` conditional blocks, which evaluate sequentially.

    if foo {
        // ...
    } elif bar {
        // ...
    } elif baz {
        // ...
    }

### Else-Then Statement ###

When no conditions are met, then the `else` conditional block will be executed.

    if foo {
        // ...
    } else {
        // ...
    }

## Iteration ##

The continuous execution of a block or the iteration of an enumerable are handled by loop statements.

### Syntax ###

    STRUCTURE
        loop {
        }

        for VARIABLE in EXPRESSION {
        [ } else { ]
        }

    VARIABLE
        VALUE | KEY, VALUE
        Refer to the variables specification.

    KEY
        The index or key of the current item within an iterable.

    VALUE
        The value of the current item within an iterable.

    EXPRESSION
        Refer to the expressions specification.

### Loop Statement ###

The popular `while` and `do-while` loops are not supported, instead we have a simple `loop` structure, which will continuously run until explicitly told to `stop`.

    loop {
        // ...

        if expression {
            stop
        }
    }

This is the same as writing `while (true)` in other languages.

### For-Loop Statement ###

The `for` loop is used for iterating over enumerables, like collections.

    for value in [1, 2, 3] {
        // ...
    }

They current index or key of the item can be accessed by inserting an additional variable separated by a comma.

    foo = { 1: 'a', 2: 'b', 3: 'c'}

    for key, value in foo {
        // ...
    }

An `else` block can be defined that will execute if the expression is false or empty.

    for value in [] {
        // ...
    } else {
        // ...
    }

#### Ranges ####

The `for` loop does not support the auto-incrementing form found in other languages, like C. However, we can create a range and loop that instead.

    for i in 0..10 {
        // 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
    }

### Flow Control ###

The `stop` statement will stop the loop.

    for value in foo {
        if expression {
            stop
        }
    }

The `next` statement will skip to the next item.

    for value in foo {
        if expression {
            next
        }
    }

## Matching ##

Pattern or value matching can be useful when bulk conditional execution is required.

### Syntax ###

    STRUCTURE
        match VARIABLE {
            BLOCK
            [ BLOCK ]
            [ ... ]
        [ } else { ]
        }

    VARIABLE
        Refer to the variables specification.

    BLOCK
        EXPRESSION { }

    EXPRESSION
        VALUE[, VALUE[, ... ]]
        Refer to the expressions specification.

### Match Statement ###

The `match` block is similar to a switch case block, in that it executes different blocks based on a matching pattern.

    var = 'foo'

    match var {
        'foo' { // ... }
        'bar' { // ... }
        'baz' { // ... }
    }

Multiple patterns are separated with a comma.

    match var {
        'foo', 'bar' { // ... }
        'baz' { // ... }
    }

When no match is found, then the `else` block will be executed. This can be used as the `default` case found in other languages.

    match var {
        // ...
    } else {
        // ...
    }

#### Variable & Reference Matching ####

Variables can also be used within the expression portion of the `match` statement.

    foo = 123
    bar = 456

    match 456 {
        foo { // ... }
        bar { // ... }
    }

#### Pattern Matching ###

Patterns via regular expressions are also supported.

    match var {
        `^foo` { // ... }
        `bar$` { // ... }
    }
