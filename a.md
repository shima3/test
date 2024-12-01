---
layout: default
---

```ebnf
Token        = Significant | Whitespace | Comment ;
Significant  = Symbol | String | "(" | ")" ;

Symbol      = SymbolChar, { SymbolChar } ;
SymbolChar  = Letter | Digit | SpecialChar ;
Letter      = "a"..."z" | "A"..."Z" | "_" ;
Digit       = "0"..."9" ;
SpecialChar = "!" | "?" | "*" | "+" | "-" | "/" | "=" | "<" | ">" | "$" | "%" | "&" | "|" | "." | "^" ;

String      = '"', { StringCharacter }, '"' ;
StringCharacter = Character | EscapeSequence ;
Character   = ? any valid character except '"', '\', and Newline ? ;
EscapeSequence  = "\", ( '"' | "\" | "n" | "t" | "r" ) ;

Digits      = Digit, { Digit } ;

Whitespace  = Space | Tab | Newline ;
Space       = " " ;
Tab         = "\t" ;
Newline     = "\n" | "\r\n" ;

Comment     = LineComment | BlockComment ;
LineComment = ";", { LineCommentCharacter }, Newline ;
LineCommentCharacter = ? any valid character except Newline ? ;

BlockComment = "#|", { BlockCommentContent }, "|#" ;
BlockCommentContent = BlockCommentText | BlockComment ;
BlockCommentText    = ? character sequence not containing #| or |# ? ;
```
