# LexerFunction
Lexer that receives a string and returns a list of tokens

Tokens are returned in the order that they were encountered in the string, according to the following rules:

**Non-tokens**
whitespace and comments are skipped and not in the token list

**Tokens**
A token is a list of two items: a symbol for type and a value of any type representing the token data.
Some token types won't have extra data, so slot will be #f. If it does, the type of the extra value is specified.

**Valid Token Types**
punctuation, number literals, string literals, keywords, names

**Punctuation**
1. parentheses, token(OPAREN) and token(CPAREN) for opening and closing
2. braces, {}, token(OBRACE) and token(CBRACE)
3. comma, as token(COMMA)
4. semicolon, as token(SEMICOLON)
5. period, as token(PERIOD)

**Number Literals**
1. Integers: one or more digit characters 0-9, represented by token(INT <value>); <value> is the parsed value of the integer
2. Floats: 1+ digit characters, represented by token(FLOAT, <value>)

**String Literals**
They begin and end with double quote character.
String literals produce a token(STRING, <contents>) where <contents> is the contents of the string literal.
  
**Keywords**
Reserved keywords listed below
1. def
2. fun
3. if
4. not
5. and
6. or

**Names**
Contain one or more non-whitespace characters.
Must not contian punctuation, contain a double quote character, or start with a digit.

**Token Boundaries**
Number literals, string literals, keywords, and names must be followed by either whitespace, punctuation, or end of input string.

**Invalid Input**
Represented as token(INVALID, <input>) where <input> is a string.
