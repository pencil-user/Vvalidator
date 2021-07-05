# Simple Validator Example

JavaScript JSON validator that both checks and transforms values. 

Usage:

We can import it by

``const V = require("./Vvalidator/validator.js``

Basic usage is ``V(value, schema)``

Simple example:

``const result = V(55, V.number(22,44))``

This will return a result object ``{value: 55}`` because everything is okay.

``const result = V(8, V.number(22,44))``

This will return a result object  ``{errors: [ 'Must be equal or higher than 11' ], value: 2 }``, because yur number is too small.


More complex example:


    const result = V(
        {
            Name:'Ivan',
            Surname:'Cvetkovic',
            Height: '188',
            DateOfBirth: '1970-11-12',
            Cars: ['toyota', 'tesla model 3']
        },
        {
            Name: V.string(3,255).required(),
            Surname: V.string(3,255).required(),
            Height: V.number(),
            DateOfBirth: V.date(),
            Cars: [V.string()]
        })


Result object will have no errors, but value property will transform Height from string to number. 

You can use ``V.body(schema)`` as express middleware. It will evaluere request body.