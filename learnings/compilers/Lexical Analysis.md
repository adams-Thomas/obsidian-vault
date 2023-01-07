First phase of a compiler.
Converts the high level input program into a sequence of Tokens.

**What are tokens?**
Lexical tokens are a sequence of characters that can be treated as a unit in the grammer of programming languages.
Examples;
- Types
- Punctuation Tokens (If, void, return, ...)
- Alphabetic/Keyword tokens

Some non-tokens are comments, macros, blanks, tabs, new lines, ...

**Top level process**
1. Tokenization - Dividing the program into valid tokens.
2. Remove white space characters 
3. Remove comments
4. Provides help in generating error messages.

