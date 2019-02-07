# A BBEdit Codeless Language Module for Swift

## Status

Keyword, comment, and string highlighting work. Classes, structs, enums, functions, and extensions are indexed. Functions can be folded.

## Installation

1. Copy the file *swift.plist* to *~/Library/Application Support/BBEdit/Language Modules*. You may have to create the *Language Modules* folder if it doesn’t exist.
2. Quit and relaunch BBEdit.

Now files with the extension “swift” should be syntax highlighted. The function pop-up menu in the navigation bar should also list all the declarations in the current file.

## Known Issues

- Extensions are only indexed by base type. This means that multiple extensions of the same base type have the same identifier in the function pop-up menu.
- Identifier matching does not include the full unicode ranges allowed by the Swift language reference. Only upper and lower case A-Z, 0-9, and ‘_’ are matched. I’m sorry for the lack of diacritic and emoji support, but I haven’t yet sorted out how to convince BBEdit to handle them in *Identifier and Keyword Character Class*.
- Only functions can be folded.
- Nested declarations are not indented in the function pop-up. I don’t think this is possible with CLMs.

## Credits

The bulk of this CLM was developed by [Curt Clifton](https://github.com/curtclifton/bbedit-swift-clm). [Michael Tsai](https://mjtsai.com) made the improvements below.

## History

- Curt’s CLM did not show functions inside of classes, structs, or extensions, which is most of the functions that I write. This was due to the fact that [BBEdit CLMs](http://www.barebones.com/support/develop/clm.html) do not support nesting. I’ve fixed this by making the `function` pattern only match the body of a `func`; for other types, it matches just up to the name. This makes it possible to show nested functions in BBEdit’s function pop-up menu. The downside is that it is no longer possible to fold classes, structs, or extensions.
- The operators `==` and `<` are now valid function names.
- Added more keywords and pre-defined names.
- Added support for triple-quoted strings.
- Class functions show the name of the function instead of `func`.
