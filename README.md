
tslint-microsoft-contrib
======

A set of [TSLint](https://github.com/palantir/tslint) rules used on some Microsoft projects.

Version 0.0.5
-------------
This software is not yet released with a 1.0 version. 
All [release blockers](https://github.com/Microsoft/tslint-microsoft-contrib/issues?q=is%3Aopen+is%3Aissue+milestone%3A1.0) are listed in the issues page.

Installation
------------

    npm install tslint-microsoft-contrib

Configuration
-------------

##### Configure your Grunt build task

Add the new rulesDirectory to your tslint task: 

    grunt.initConfig({
      tslint: {
        options: {
          rulesDirectory: 'node_modules/tslint-microsoft-contrib',
          configuration: grunt.file.readJSON("tslint-contrib.json")
        },
        files: {
          src: ['src/file1.ts', 'src/file2.ts']
        }
      }
    })

The tslint-contrib.json file follows the same conventions as other tslint rules. 

Supported Rules
-----

A sample configuration file with all options is available under tslint-microsoft-contrig/tslint.json


Rule Name   | Description | Since  
:---------- | :------------ | -------------
`export-name`                   | The name of the exported module must match the filename of the source file. This is case-sensitive but ignores file extension. Since version 0.0.5, this rule takes a list of regular expressions as a parameter. Any export name matching that regular expression will be ignored. For example, to allow an exported name like myChartOptions, then configure the rule like this: "export-name": \[true, "myChartOptionsg"\]| 0.0.3
`jquery-deferred-must-complete` | When a JQuery Deferred instance is created, then either reject() or resolve() must be called on it within all code branches in the scope. For more examples see the [feature request](https://github.com/Microsoft/tslint-microsoft-contrib/issues/26). | 0.0.5
`missing-jsdoc`                 | All files must have a top level [JSDoc](http://usejsdoc.org/) comment. A JSDoc comment starts with /** (not one more or one less asterisk) and a JSDoc at the 'top-level' appears without leading spaces. Trailing spaces are acceptable but not recommended. | 0.0.5
`missing-optional-annotation`   | A parameter that follows one or more parameters marked as optional is not itself marked optional | 0.0.1
`no-banned-terms`               | Do not use banned terms: [caller](https://msdn.microsoft.com/library/7t96kt3h(v=vs.94).aspx), [callee](https://msdn.microsoft.com/library/334e1zza(v=vs.94).aspx), [eval](https://msdn.microsoft.com/library/12k71sw7(v=vs.94).aspx), [arguments](https://msdn.microsoft.com/library/he95z461(v=vs.94).aspx). These terms refer to functions or properties that should not be used, so it is best practice to simply avoid them. | 0.0.1
`no-cookies`                    | Do not use cookies | 0.0.1
`no-delete-expression`          | Do not delete expressions. Only properties should be deleted | 0.0.2
`no-disable-auto-sanitization`  | Do not disable auto-sanitization of HTML because this opens up your page to an XSS attack. Specifically, do not use the [execUnsafeLocalFunction](https://msdn.microsoft.com/en-us/library/windows/apps/hh767331.aspx) or [setInnerHTMLUnsafe](https://msdn.microsoft.com/en-us/library/windows/apps/br211696.aspx) functions. | 0.0.1
`no-document-write`             | Do not use document.write | 0.0.1
`no-duplicate-parameter-names`  | Do not write functions or methods with duplicate parameter names | 0.0.1
`no-empty-interfaces`           | Do not use empty interfaces. They are compile-time only artifacts and they serve no useful purpose | 0.0.5
`no-exec-script`                | Do not use the execScript functions | 0.0.1
`no-function-constructor-with-string-args` | Do not use the version of the Function constructor that accepts a string argument to define the body of the function | 0.0.1
`no-http-string`                | Do not use strings that start with 'http:'. URL strings should start with 'https:'. Http strings can be a security problem and indicator that your software may suffer from cookie-stealing attacks. Since version 0.0.5, this rule takes a list of regular expressions as a parameter. Any string matching that regular expression will be ignored. For example, to allow http connections to example.com and examples.com, configure your rule like this: "no-http-string": \[true, "http://www.example.com/?.*", "http://www.examples.com/?.*"\]| 0.0.3
`no-increment-decrement`        | Avoid use of increment and decrement operators particularly as part of complicated expressions | 0.0.1
`no-missing-visibility-modifiers` | Class members (both fields and methods) should have visibility modifiers specified. THe Principle of Least Visibility guides us to prefer private methods and fields when possible. If a developer forgets to add a modifier then TypeScript assumes the element should be public, which is the wrong default choice. | 0.0.5
`no-multiline-string`           | Do not declare multiline strings | 0.0.1
`no-octal-literal`              | Do not use octal literals or escaped octal sequences | 0.0.1
`no-reserved-keywords`          | Do not use reserved keywords as names of local variables, fields, functions, or other identifiers. | 0.0.1
`no-string-based-set-immediate` | Do not use the version of setImmediate that accepts code as a string argument. However, it is acceptable to use the version of setImmediate where a direct reference to a function is provided as the callback argument | 0.0.1
`no-string-based-set-interval`  | Do not use the version of setInterval that accepts code as a string argument. However, it is acceptable to use the version of setInterval where a direct reference to a function is provided as the callback argument | 0.0.1
`no-string-based-set-timeout`   | Do not use the version of setTimeout that accepts code as a string argument. However, it is acceptable to use the version of setTimeout where a direct reference to a function is provided as the callback argument | 0.0.1
`no-unnecessary-semicolons`     | Remove unnecessary semicolons | 0.0.1
`no-unused-imports`             | Remove unused imports | 0.0.1
`no-with-statement`             | Do not use with statements. Assign the item to a new variable instead | 0.0.1
`prefer-array-literal`          | Use array literal syntax when declaring arry types instead of the Array object with a generic parameter type. For example, prefer the Javascript from of string[] to the TypeScript form Array<string> | 0.0.5
`react-no-dangerous-html`       | Do not use React's dangerouslySetInnerHTML API. This rule finds usages of the dangerouslySetInnerHTML API (but not any JSX references). For more info see the [react-no-dangerous-html Rule wiki page](https://github.com/Microsoft/tslint-microsoft-contrib/wiki/react-no-dangerous-html-Rule). | 0.0.2
`use-named-parameter`           | Do not reference the arguments object by numerical index; instead, use a named parameter. This rule is similar to JSLint's [Use a named parameter](https://jslinterrors.com/use-a-named-parameter) rule. | 0.0.3


Development
-----------

To develop tslint-microsoft-contrib simply clone the repository, install dependencies and run grunt:

    git config --global core.autocrlf input
    git config --global core.eol lf
    git clone git@github.com:Microsoft/tslint-microsoft-contrib.git
    cd tslint-microsoft-contrib
    npm install
    grunt all
    grunt create-rule --rule-name=no-something-or-other
    
Debug code
-----------
If command fails because of file access permissions, prefix it with sudo.

    npm install -g node-inspector
    node-inspector

In another terminal window run:

    # on *nix machines: 
    node --debug-brk /usr/local/bin/grunt mochaTest
    # on Windows machines: 
    node --debug-brk /c/Users/[your alias]/AppData/Roaming/npm/node_modules/grunt-cli/bin/grunt
    
Open in browser:
    
    http://127.0.0.1:8080/?ws=127.0.0.1:8080&port=5858
    
Set a breakpoint somewhere in your code and resume execution. Your breakpoint should be hit.

Creating a new Release
----------------------

Refer to the [Releases Wiki Page](https://github.com/Microsoft/tslint-microsoft-contrib/wiki/Releases)