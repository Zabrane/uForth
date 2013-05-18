uForth
======

Micro Forth (uForth), a model-based implementation of a Forth-like
language interpreter in Java and Erlang.

## Introduction ##

This repository contains three projects:

- **uForth** (under the directory `eclipse-juno-workspace`): Includes
  the Eclipse Modeling Framework (EMF) Ecore meta-model representing
  static instances of a uForth program. It also includes a reader (a
  program that interprets uForth programs and converts them into
  instances of the uForth metamodel) and an interpreter (incomplete by
  now, but easily understandable).
- **uForthProgGen** (under the directory `eclipse-juno-workspace`):
  Includes a Xpand program that converts instances of the uForth
  metamodel into the original program (modulo comments and
  indentation). It is used to show my students how to process a model
  to generate code. It could be used to generate machine code (a
  compiler, for instance) or, as the assignment for my students, to
  generate Erlang code that uses the next project to run.
- **forth_interpreter.erl** (under the directory `erlang`): It
  includes an Erlang interpreter for the uForth language. The
  interpreter is able to run programs, but it does not contain a
  reader, so programs have to be input using the module API. I'll show
  examples below.

## uForth ##

uForth (micro-Forth) is a variant of
[Forth](http://www.forth.com/starting-forth/) that treats strings as
an independent token. Also, it only includes one type of number, a
double precision floating point number (similar to a Java `double`).
So, an uForth program is a sequence of *words*. A *word* in uForth can
be of three different types:

- **Strings**: Any set of characters delimited by double quotes. For
  example `"Hello"`.
- **Numbers**: Double precision floating point number. Ex: `1.23`.
- **Identifiers**: Any set of chars not included within the two above
  word types. Usually in upper case. For instance, `DUP`.

As in normal Forth, definitions start with the word `:` and end with
the word `;`. Finally, programs end with `END`.

Following the examples in the cited Starting Forth, an example uForth
program that can be used as reference is:

    : STAR 42 EMIT ;
    : STARS 0 DO STAR LOOP ;

    20 STARS END

The previous program writes 20 stars in the screen.


