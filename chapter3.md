# Namespaces and Modules

namespace Shapes {
    export namespace Polygons {
        export class Triangle { }
        export class Square { }
    }
}

import polygons = Shapes.Polygons;
vs
var polygons = Shapes.Polygons;

Notice that we don't use the require keyword; instead we assign directly from the qualified name of the symbol we're importing. 
This is similar to using var, but also works on the type and namespace meanings of the imported symbol. 
Importantly, for values, import is a distinct reference from the original symbol, so changes to an aliased var will not be reflected in the original variable.

Import a module in another module
import myModule = module("muModule");//Name of the file

declare var myVar; is how to declare a variable that exists somewhere in the JS

In TypeScript, any file containing a top-level import or export is considered an (external) module,
the files themselves constitute a module and are identified by their filenames.

(External) modules require a module loader to be present. If you run this in your browser you have to take care of including a module loader yourself. 

TypeScript declarations file (ex. jquery.d.ts) using the /// <reference path="..."/> syntax, 
it's up to me to make sure I load the corresponding library by some other means,
 i.e. just referencing the .d.ts file doesn't load the library.
 
 When you’re writing TypeScript code that needs access to ambient declarations, a special reference comment must be added to the top of the module that needs it:
Triple slash directives are needed only if you don't have a tsconfig.json file where you should specify the files that the compiler should include in compilation.
Otherwise you should use triple slash to indicate dependencies of each file.

/// <reference path="jquery" />
The path given in the reference comment can be either a standard module ID or a path to a file. If you use a filesystem path and get an error about TypeScript not being able to resolve the path, make sure that you have not accidentally typoed .ts as .js.

When writing modular code, reference comments should only ever be used to import ambient declarations; all other dependencies should be loaded using the import keyword. Happily, dependencies loaded using import that are never used, or that are only used for compile-time checks, will be intelligently excluded from the compiler output.


In "/// <reference path " is not case sensitive, so capital letters does not matter


The import statement tells the system it can get an AppComponent from a module named app.component located in a neighboring file. 
The module name (AKA module id) is often the same as the filename without its extension.

TypeScript added support for ES6 modules in version 1.5. 
TypeScript can be configured in two different ways: --target es6 or --target es5 --module commonjs. 


WARNING: "module X { is equivalent to the now-preferred namespace X {";

At runtime the module loader is responsible for locating and executing all dependencies of a module before executing it. Well-known modules loaders used in JavaScript are the CommonJS module loader for Node.js and require.js for Web applications.
In TypeScript, just as in ECMAScript 2015, any file containing a top-level import or export is considered a module.

can only be one default export per module.
Default export class and function declaration names are optional.

Both CommonJS and AMD generally have the concept of an exports object which contains all exports from a module.TypeScript supports export = to model the traditional CommonJS and AMD workflow.The export = syntax specifies a single object that is exported from the module. When exporting a module using export =, TypeScript-specific import module = require("module") must be used to import the module.

Namespace
--------
namespaces are handy for grouping together logically-related objects and types in the global scope. 
 Modules, on the other hand, are already present in a file system, necessarily. We have to resolve them by path and filename, so there’s a logical organization scheme for us to use.
Namespaces are important to avoid naming collisions in the global scope. For example, you might have My.Application.Customer.AddForm and My.Application.Order.AddForm – two types with the same name, but a different namespace. This, however, is not an issue with modules. Within a module, there’s no plausible reason to have two objects with the same name. From the consumption side, the consumer of any given module gets to pick the name that they will use to refer to the module, so accidental naming conflicts are impossible.

we’ll split our Validation namespace across many files. Even though the files are separate, they can each contribute to the same namespace and can be consumed as if they were all defined in one place. Because there are dependencies between files, we’ll add reference tags to tell the compiler about the relationships between the files.

Multiple files that have the same export namespace Foo { at top-level (don’t think that these are going to combine into one Foo!)
-----
namespace Shapes {
    export namespace Polygons {
        export class Triangle { }
        export class Square { }
    }
}

import polygons = Shapes.Polygons;
let sq = new polygons.Square(); // Same as 'new Shapes.Polygons.Square()'

Not to be confused with the import x = require("name") syntax used to load modules.
This is similar to using var, but also works on the type and namespace meanings of the imported symbol. 
-----
Just like namespaces, modules can contain both code and declarations. The main difference is that modules declare their dependencies.

Modules also have a dependency on a module loader.

Questions:
1- when to use "declare module 'Foo' {} " => Creates ambient module 'Foo', without quotes creates a namespace (only ambient modules can use quoted names)
2- when to use "declare namespace  Foo{} " 
	=> Creates ambient namespace
	This declares that there exists namespace Foo, defined in some external file (not included in the current compilation), allowing to use Foo which is assumed to contain things declared within {} (and {} may contain only declarations, not definitions here)
	
3- when to use "namespace  Foo{} "  => Simply creates a namespace
4- when to use "export namespace  Foo{} " => Creates a module which contains the namespace

Notes on questions:
-module Foo { } and  namespace Foo { } are exactly the same (both namespaces).
-export module Foo { } and   export namespace Foo { } are exactly the same(both namespaces).
-declare module Foo {} is the same with declare namespace Foo {}

The declare keyword is used for ambient declarations where you want to define a variable that may not have originated from a TypeScript file
When using declare Initializers are not allowed in ambient context.
example 
declare namespace Foo {
    var t = 6; //error
}