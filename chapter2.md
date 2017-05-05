# General

When we add public or private accessibility to an argument of the constructor, that argument automatically becomes a member of the class with the relevant accessibility modifier.

name?: string   Name is optional
In TypeScript, each member is public by default. 

In TypeScript you can have only one constructor per class.
That is a departure from ES6 which allows one class to have more than one constructor as
long as they have a different number of parameters.



self is really window.self
If you're using a function in a different context, this will refer to that context, but self will still be window.

type CardinalDirection = "North" | "East" | "South" | "West";


interface Foo {
    bar: number;
    bas: string;
}
var foo = {} as Foo;

readOnly vs const
The difference is that the value of a static readonly field is set at run time, and can thus be modified by the containing class, whereas the value of a const field is set to a compile time constant.



readOnly: boolean | 'nocursor';