# tsconfig.json

Specifies the root files and the compiler options required to compile the project. The presence of a tsconfig.json file in a directory indicates that the directory is the root of a TypeScript project.  


By invoking tsc with no input files, the compiler searches for the tsconfig.json When input files are specified on the command line, tsconfig.json files are ignored. Using the "files" property in tsconfig to specify files to compile, if files are missing, all files are included. If the "files" and "include" are both left unspecified, the compiler defaults to including all TypeScript \(.ts, .d.ts and .tsx\) files in the containing directory and subdirectories except those excluded using the "exclude" property. If the "files" or "include" properties are specified, the compiler will instead include the union of the files included by those two properties. Files included using "include" can be filtered using the "exclude" property. However, files included explicitly using the "files" property are always included regardless of "exclude".

