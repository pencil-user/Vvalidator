# Simple Validator Example

JavaScript JSON validator that both checks and transforms values. 

Usage:

We can import it by

``const V = require("./Vvalidator/validator.js``

Simple example:

``const result = V(55, V.number(22,44))``

This will return a result object that only consists of value property that is 55.

``const result = V(77, V.number(22,44))``

This will return a result object that consists of value propert and error property, because 77 is bigger than 44.


More complex example:

``
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
``

Result object will have no errors, but value property will transform Height from string to number. 