# Lambda-Prolog-Tutorial
A tutorial for the beautiful programming language lambdaprolog


Lambda-Prolog must not die. Recently the mailing list maintained by Gopalan Nadathur has been closed after operating for over 25 years and the main implementation called "Teyjus" seems to have stopped being maintained. Lambda-Prolog is wonderful programming language and this repository serves as a place learn it. I hope for the survival of the programming language.

## Higher Order Logic Programming (HOLP)

The basis for lambda prolog is higher order logic. This is achieved through types and sequent calculus. In lambda prolog there are only 6 types: int, real, o, string, in_stream, out_stream, all starting with a lower case letter in ever instance. Beyond types are type constructors which belong before type in an expression, type constructors are things like list also starting with a lower case letter. To define a type with a type constructor we would write "constructor type", as an example, we could write "list int" or "list string".

Afterwards we should consider type constructors. Type constructors allow us to define new types. If we wanted to define a type we could do so like this:
```
type identifier int -> list int -> o.
```
Notice how we put a period at the end of the expression. A period in lambda prolog is akin to a semi-colon in a language like java and is only there to tell the compiler when the expression ends. In lambda prolog, the '->' symbol associates the right meaning that
```
type identifier int -> list int -> o.
```
is equivalent to
```
type identifier int -> (list int -> o).
```
Knowing this we should move into kind expressions. Kind expressions are similar to types but allow us to define kinds. We can define a kind like this:
```
kind identifier type -> type -> type.
```
With kind expressions the first type is to be distinguished from the rest. When we call this identifier the first type will be the indentifiers name and then rest with be parameters. This is done because kind expressions associate the left instead of the right as type constructors do although it should be noted that this associativity is not strict and can be controlled with the use of parenthesis. Let us define a kind:
```
kind pair type -> type -> type.
```
We can then add pair to a type constructor like this:
```
type name pair int string -> o.
```
Fortunately, the true beauty of lambda prolog is beginning to show already. With the little we have learned there is already so much to think about. For starters we should discuss the relationship between type constructors and kind constructors. One would initially expect them to be quite similar but there is a reason they are the way they are. Kind expressions encourage the use of the type keyword for flexibility. Type constructors can then use them with any type or type constructors even those defined with kind expressions if they have arity of 0 which we will get into later. This makes sense too as you will realize. When we think about the associativity in type constructors and kind constructors we begin to see something interesting. With kind constructors we left associativity moves into the identifier which is great when calling it. But we dont call type constructors in type constructors so when we add an o the end which means formula, we are moving the paramters into the formula. Meanwhile having different associativity options in certain situations can allow us to write more readable code as we dont need insane parenthesis. Now lets discuss data structures. Suppose we wanted to make a tree structure in lambda prolog using type and kind constructors. We could do so like this:
```
kind tree type -> type.
type empty tree T.
```
Now would be a good time to mention that lambda prolog support polymorphism so T is polymorphic. If we wanted to then define a node we could do so like this:
```

```
