# Monkey programming language interpreter 
### this repo is a result to the book (Writing an interpreter in GO by Ball thorson)

## Monkey has the following:
• C-like syntax
• variable bindings
• integers and booleans
• arithmetic expressions
• built-in functions
• first-class and higher-order functions
• closures
• a string data structure
• an array data structure
• a hash data structure

## the interpreter will have :
• the lexer
• the parser
• the Abstract Syntax Tree (AST)
• the internal object system
• the evaluator

## Why Go:

- Go is mid as f*ck and that's why it is the best fit for literally everything, and especially an interpreter where you only write an algorithm that will execute certain stuff in order you don't need a fancy UI or an edge cutting performance, you just need to write code.

- Go does not change so much on updates that's another reason your code will survive for years.


# Chapter 1 : LEXING

Source Code --[ Tokenizer ]--> Tokens --[ Parser ]--> Abstract Syntax

### Defining our tokens:

Monkey is simple and concise we're not gonna store the numbers of lines, columns, we just gonna keep it plain and simple.

Token data structure:
inside the file below you can find the `Token` definition and the token types we have in our project
> token/token.go
```go
type TokenType string

type Token struct {
	Type    TokenType
	Literal string
}
```

>[!IMPORTANT]
> in a production environment it makes sense to attach filenames and line numbers to tokens, to better track down lexing and parsing errors. So it would be better to initialize the lexer with an io.Reader and the filename. But since that would add more complexity we’re not here to handle, we’ll start small and just use a string and ignore filenames and line numbers.
