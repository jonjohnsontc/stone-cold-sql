# Stone Cold SQL

My quest to make a SQL dialect based on Stone Cold's most popular words and phrases. I would like to get this potentially working against Trino, Spark, and Postgres systems. I think it's possible for me to be 'lazy' and only make a lexer/parser for Trino and Spark, since they can connect to postgres (edit: I think it really depends on how Trino and Spark communicate with postgres)

SELECT -> YOU GOT  
JOIN -> WHAT  
COMMIT -> AND THAT'S THE BOTTOM LINE CAUSE STONE COLD SAID SO  

## Definitions

Lexer: converting text into tokens
Parser: digs through the tokens to check for valid syntax and builds a parse tree after

## How

I think I can do it by changing the lexers and parsers for each database to interact with Stone Cold's phrases.

Although, perhaps I only need to adjust the lexer, since I just want the stone cold text to convert to the same tokens that are generated when using ANSI SQL syntax.
