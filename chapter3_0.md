# imports

The import statement is used to import bindings which are exported by another module.
Ref. https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/import


## Syntax
```
import defaultExport from "module-name";
import * as name from "module-name";
import { export } from "module-name";
import { export as alias } from "module-name";
import { export1 , export2 } from "module-name";
import { export1 , export2 as alias2 , [...] } from "module-name";
import defaultExport, { export [ , [...] ] } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name";
```

#### defaultExport

Name that will refer to the default export from the module (one per module).

#### module-name

The module to import from. This is often a relative or absolute path name to the .js file containing the module, excluding the .js extension. Certain bundlers may permit or require the use of the extension;

#### name

Name of the module object that will be used as a kind of namespace when referring to the imports.

#### export, exportN

Name of the exports to be imported (specify individual named exports).

#### alias, aliasN

Names that will refer to the named imports.


The export parameters specify individual named exports, while the import * as name syntax imports all of them.
