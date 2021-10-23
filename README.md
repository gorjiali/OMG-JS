# JS

* __Primitive and non-primitive types__: All we mean by *primitive* is that it is like literally written as an actual value (*number*, *string*, *boolean*, *null*, *undefined*and *symbol*) rather than *non-primitive* that is a collection of values (*object*).

* __Binary and unary operator__: Those kinds of operators, ones that has a left and a right in terms of their operands are called *binary operators* and *unary operator* means a single operand involved in the operation.

* __Expressions and Statements__: An *expression* is like a phrase, and a *statement* is like a whole sentence, entire thing from beginning to the final. for example in ```age = 1 + (age * 2);``` we have a *statement* that contains several *expressions* like ```2``` (*literal expression*), ```(age * 2)```, ```age = 1 + (age * 2)``` (*assignment expression*).

* __In javascript, everything is an object__: completely false!

* __In javascript, variables don't have types, values do.__

* __*undefined* type__: if variable only declared and has no value (```var b;```) or when the variable has never been declared; 

* __*function* type?!__ *function* is not an actual primitive type, its a subtype of *object*, but for ```typeof``` operator it does have its own unique return value!

* __NaN__: *invalid number* and no *not a number*, because a *string* is also a *not a number*.

* __Fundamental Objects__: Many of these are ones that actually comes historically, they were copied from a language like java (```Object()```, ```Array()```, ```Function()```, ```Date()```, ```RegExp()```, ```Error()```), we use ```new``` keyword to instantiate instances of those (object representation), but we have some of other fundamental objects that we don't want to use ```new``` keyword (```String()```, ```Number()```, ```Boolean()```) and use those as function because if we call them with some value, it actually change it into that type.

* __Coercion__: The way to convert from one type to another.

* __Truthy and Falsy__: *Falsy* means which values if we try to convert them into boolean well becom ```false``` (```""```, ```0```, ```null```, ```NaN```, ```false```, ```undefined```) and *Truthy* means which values if we try to convert them into boolean will become ```true``` (everything else).

* __Coercion Best Practice__: A quality JS program embraces coercion, <strong>making sure the types involved in every operation are clear</strong>.

* __```==``` vs ```===```__: ```==``` allows coercion (types different) and ```===``` disallows coercion (types same). when the types are already the same, the dobule equals and triple equals do the exactle the same thing in 100% of all cases. ```===``` is not about comparisons with unknown types, it is about comparisons with known type(s), optionally where conversion are helpful.

* __Scope__: Well-defined set of rules for storing variables in some location, and for finding those variables at a later time.

* __function expressing__: a function expression is a function that is assigned as a value somewhere. ```var clickHandler = function() { ... }``` (*anonymous function expression*) or ```var clickHandler = function clickHandler() { ... }``` (*named function expression*), best way to identify a *function expression* is: function expressions can be anonymous, but function declarations cannot omit the name. (always use *named function expression* in all cases ;))

  * __Immediately Invoked Function Expression (IIFE)__: declaring and running immediately a function in a new block. ```(function anotherTeacher() { ... })();```. that allows us to encapsulate some of out behaviors and things so that they don't pollute other parts of program.