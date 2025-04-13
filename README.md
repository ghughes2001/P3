# P3

Project P3: Static Semantics
Due April 17, 2025
Total 50 points.
• Check static semantics assuming global scope for variables.
• Use a symbol table to track variables and check semantics.
• Variables
o For our project, both “ and # declare a variable and allocate memory
o Variables are t2 type tokens (begin with + followed by one or more digits)
Requirements
• The only static semantics we impose are proper use of variables.
o Variables must be defined before used first time (must satisfy syntax too)
o Variable name can only be defined once
• Invocation:
> P3 [file]
• Modify the main function so that after calling parser and receiving the tree, main will call the static
semantic function on the tree.
• If an error is encountered, state the type of error (using an undefined variable or redefining a variable)
and the variable name
o You may terminate when you find the first error.
• If there are no errors, output the symbol table.
• Failure to compile or wrong invocations will not be graded.
• Program must compile and run on hellbender
• Graded 50% execution, 40% comments, and 10% structure/standards.
Suggestions
Software support
• Use any container for storing identifiers such as array, list, etc. with the following interface. Below we
show ‘String’ as the parameter, which is the ID token instance, but it could include line number or the
entire token for more detailed error reporting. This container will process identifier tokens only.
o insert(String) - insert the string if not already there or error if already there (you may return fail
indication or issue detailed error here and exit)
o Bool verify(String) - return true if the string is already in the container and false otherwise
(suggest you return false indicator rather than issue detailed error with exit, but either way
could possibly work if you assume that no one checks verify() unless to process variable use)
Static semantics
• Instantiate symbol table
• Traverse the tree
• If you encounter a variable declaration, attempt to insert into your symbol table
• If you encounter a variable that is not being declared, verify that it already exists in the symbol
table
Test Files
Good file example:
( # +136 $ +136 )
Symbol Table:
+136
Another good file example:
“ +5 ( +5 % k10 $ +5 )
Symbol Table:
+5
Bad file example:
( # +136 $ +5 )
