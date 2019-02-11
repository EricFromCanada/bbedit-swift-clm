# A BBEdit Codeless Language Module for Swift

## Status

Keyword, comment, number, and string highlighting work. Classes, structs, enums, functions, and extensions are indexed. Functions can be folded.

## Installation

1. Copy the file *swift.plist* to `~/Library/Application Support/BBEdit/Language Modules`. You may have to create the *Language Modules* folder if it doesn’t exist.
2. Quit and relaunch BBEdit.

Now files with the extension `swift` should be syntax highlighted. The function pop-up menu in the navigation bar should also list all the declarations in the current file.

## Known Issues

- Extensions are only indexed by base type. This means that multiple extensions of the same base type have the same identifier in the function pop-up menu.
- Identifier matching does not include the full Unicode ranges allowed by the Swift language reference. Only code points below U+10000 are matched. Emoji and other four-byte characters cannot be matched by the PCRE library that BBEdit is currently compiled with.
- Only functions can be folded.
- Nested declarations are not indented in the function pop-up, which is only possible with compiled language modules.
- Since BBEdit as of 12.5 ships with a Swift language module, it would need to be disabled to continue using this one. This can be done by removing *Swift.bblm* from `BBEdit.app/Contents/PlugIns/Language Modules` and relaunching BBEdit.

## Credits

The bulk of this CLM was developed by [Curt Clifton](https://github.com/curtclifton/bbedit-swift-clm). [Michael Tsai](https://mjtsai.com) and [@EricFromCanada](https://github.com/EricFromCanada) made the improvements below.

## History

- Curt’s CLM did not show functions inside of classes, structs, or extensions, which is most of the functions that I write. This was due to the fact that [BBEdit CLMs](http://www.barebones.com/support/develop/clm.html) do not support nesting. I’ve fixed this by making the `function` pattern match both the name and body of `func` blocks only; for other types, it matches just up to the name. This makes it possible to show nested functions in BBEdit’s function pop-up menu. The downside is that it is no longer possible to fold classes, structs, or extensions.
- All overloadable or custom operators are now valid function names.
- Keywords and pre-defined names are updated for Swift 4.2.
- Added support for triple-quoted strings and backticks around function names.
- Class functions show the name of the function instead of `func`.
