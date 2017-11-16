# General

In TypeScript, each member is public by default and you can have only one constructor per class. That is a departure from ES6 which allows one class to have more than one constructor as long as they have a different number of parameters.

When we add _public _or _private _accessibility to an argument of the constructor, that argument automatically becomes a member of the class with the relevant accessibility modifier.

`name?: string`   Name is optional

> self is really window.self  
> If you're using a function in a different context, this will refer to that context, but self will still be window.

### Create a new type

`type CardinalDirection = "North" | "East" | "South" | "West";`

### Cast an object to a new type

`interface Foo {  
    bar: number;  
    bas: string;  
}  
var foo = {} as Foo;`

### readOnly vs const
Reassignment of variable is not possible. But you can change properties of an object.

The difference is that the value of a static readonly field is set at run time, and can thus be modified by the containing class, whereas the value of a const field is set to a compile time constant.

`readOnly: boolean | 'nocursor';`

### ReadonlyArray
TypeScript comes with a ReadonlyArray<T> type that is the same as Array<T> with all mutating methods removed, so you can make sure you don’t change your arrays after creation:
    
`const arr: ReadonlyArray<number> = [1, 2, 3, 4];`

Use const or readonly, along with ReadonlyArray to make array immutable.

### Function Types
To describe a function type with an interface, we give the interface a call signature. This is like a function declaration with only the parameter list and return type given.

`interface SearchFunc {
    (source: string, subString: string): boolean;
}`

### Indexable Types
Indexable types have an index signature that describes the types we can use to index into the object, along with the corresponding return types when indexing.

`interface StringArray {
    [index: number]: string;
}

let myArray: StringArray;
myArray = ["Bob", "Fred"];`
