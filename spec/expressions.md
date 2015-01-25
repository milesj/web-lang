# Expressions #

When a type is used within an expression, the `isEmpty()` or `isNotEmpty()` methods are called. These methods 
attempt to verify the truthiness or falsiness of a value. A value is truthy if it abides the following rules:

* A boolean that is true
* A string that is not empty
* An integer or float that is not 0
* A compound who's length is not 0

Take the following if block for example:

    if 123 and 'foo' {
    
This is functionality equivalent to the following if it was written as objects.

    if 123.isNotEmpty() and 'foo'.isNotEmpty() {
