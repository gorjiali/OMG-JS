# JS

* __Primitive and non-primitive types__: All we mean by *primitive* is that it is like literally written as an actual value (*number*, *string*, *boolean*, *null*, *undefined*and *symbol*) rather than *non-primitive* that is a collection of values (*object*).

* __Binary and unary operator__: Those kinds of operators, ones that has a left and a right in terms of their operands are called *binary operators* and *unary operator* means a single operand involved in the operation.

* __Expressions and Statements__: *statement* is a group of words, numbers, and operators that performs a specific task and an *expression* is any reference to a variable or value, or a set of variable(s) and value(s) combined with operators. *Statements* are made up of one or more *expressions*. an *expression* is like a phrase, and a *statement* is like a whole sentence, entire thing from beginning to the final. for example in ```age = 1 + (age * 2);``` we have a *statement* that contains several *expressions* like ```2``` (*literal expression*), ```(age * 2)```, ```age = 1 + (age * 2)``` (*assignment expression*).

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

* __Block Scoping__: the more common way for us to organize a set of variables instead of having them pollute the enclosing scope, the outer scope, is we use what's called *block scoping*. for example instead of using *IIFE*, now we have the option to simply using a *curly brace block* but we must switch from using ```var``` to ```let```.(kyle's opinion: I like to still use ```var``` at the function level and only use ```let``` inside of blocks). it's really important for us to be very careful about not just putting something at the *function scope* because it is convenient. if it's only needed for few lines, go ahead and put a *curly brace block* about those instead of just making those at the function level (and use ```let```).

* __Closure__: Closure is when a function *remembers* the variables outside of it, even if you pass that function elsewhere. for example:
   * ```
      function ask(question) {
         setTimeout(function waitASec() {
            console.log(question);
         }, 1000);
      }

      ask("What is your name?");
      ```
      in this example, ```question``` variable is not inside of ```waitASec``` function. it's created in the outer scope of the function ```ask```. now when we run ```ask```, we pass in a string and then we call this ```setTimeout```, immediately after we call the ```setTimeout```, the ```ask``` function has finished, it's completely done, and we would normally think that all of variables inside of that go away when function done, but the reason it doesn't is because the timer is still waitig for 1000 miliseconds with a function called ```waitASec``` in its memory, and that ```waitASec``` refrencing ```question``` and as a result of that is keeps the ```question``` variable, it keeps that scope alive and that magic, the way that works, that is called closure. it is said that ```waitASec``` as a function has closure over the ```question``` variable. so that allows us to remember some variable, remember the value that's in that variable, event when our function gonna get executed in a entirely different place, and sometimes in a entirely different timeline. 
      
   * another example:

      ```
      function ask(question) {
         return function holdYourQuestion() {
            console.log(question);
         };
      }

      const myQuestion = ask("how are you?");

      myQuestion();
      ``` 

* __this__: A function's ```this``` keyword, refrences the execution context for that call, determined entirely by <strong>how the function was called</strong>. so a *this-aware function* can thus have a defferent context each time it's called (*dynamic context*), witch makes it more flexible and reusable.

* __Prototypes__: it is an object where any instances of the related *class* are going to be linked to or to deligate to (very, very brief nutshell of prototypal class object).

* __class__: the *class* keyword is layered on top of the *prototype* system and it gives us some syntax that looks a lot more like the *class* designs that we normally do in langs like C++ or Java. for example:
   * ```
      class Workshop {
         constructor(teacher) {
            this.teacher = teacher;
         }
         ask(question) {
            console.log(this.teacher, question);
         }
      }

      var deepJS = new Workshop("Kyle ");
      var reactJS = new Workshop("Susy ");

      deepJS.ask("how are you?");
      reactJS.ask("what time is it?");
      ```
      It's important to note that under the covers, javascript making the *prototype object* and making a *constructor function* and when we call ```new Workshop```, we are making a *deepJS* object that does not have an *ask* method but *deepJS* object that linked to the *prototype object* of the *Workshop class* that does have the *ask* method. That is why when we say ```deepJS.ask(...)``` we are prototype delegating to the Workshop defenition (AKA the Workshop prototype). you can see the under-the-cover mechanism in the below but *class* syntax in the top is cleaner:

      ```
      function Workshop(teacher) {
         this.teacher = teacher;
      }

      Workshop.prototype.ask = function (question) {
         console.log(this.teacher, question);
      } 
      var deepJS = new Workshop("Kyle ");
      var reactJS = new Workshop("Susy ");

      deepJS.ask("how are you?");
      reactJS.ask("what time is it?");
      ```