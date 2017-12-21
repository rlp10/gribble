# Gribble

Gribble is a text preprocessor written in Gerbil Scheme.

It consists of a library, which can be used be other Gerbil programs,
as well as an executable program which can be used to process text
files.

It is currently pre-alpha software. Nothing works here yet.

## Syntax

The syntax is inspired by Scribble, the document processing software
included as part of Racket. It uses a tilde ("~"), rather than an
arobase ("@") so as to interfere less frequently with typical writing.

Generally, the markup is processed as scheme and, if the return is not
void, then the original input text is replaced with the output. For
example, all the following would output "Hello WORLD!":

    ;; Everything in brackets is run as Scheme
	Hello ~(upcase "world")! 

	;; A function that takes one or more strings can be called with
    curly brackets
	Hello ~upcase{world}!
	
	;; A function can be given arguments other than strings using
	square brackets
	Hello ~upcase["world"]!
	
	;; You can combine square and curly braces for functions taking
	multiple arguments
	Hello ~upcase["wor"]{ld}!

In the above example, upcase is a function which takes one or more
strings, converts them to upper case and then appends them together.

## Roadmap

- Produce a function "preprocess" that takes a string and outputs a
  string, implementing each of the syntax types above

- Give preprocess an optional keyword argument which changes the
  special character "~" to something else.

- Produce some helper functions, such as "include" which includes
  and preprocesses another file by either a relative or absolute path
  
- Produce a command line program "gribble" which can do the above from
  the command line, using standard input and output.

## Future Development Ideas

- Add metadata to documents

- Add functions for creating documentation, to be output to HTML

- Allow conversion of documents to PDF, through LaTeX
