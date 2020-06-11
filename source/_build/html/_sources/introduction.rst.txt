Introduction
============

This is the specification for Rum, a lightweight and performant general-purpose scripting programming language designed to
harness the powerful ideals of functional programming, without the learning curve.

Conformance
============

An implementation of Rum is consisidered conforming when it:

* correctly handles all types, values, and functions, and all program syntax and semantics as described in this specification; 

* interprets the source code input in conformance with the latest Unicode Standard.

Grammars
========

Context-Free Grammars
---------------------

*Context-free grammars* consist of a number of *productions*. Each production has a symbol called a *nonterminal* as its *left-hand side*,
and a sequence of one or more nonterminal and *terminal* symbols as its *right-hand side*. For each grammar, the terminal symbols are 
drawn from a specified *alphabet*.

Starting from a sentence consisting of a single distinguished nonterminal, called the *goal symbol*, a given context-free grammar specifies
a *language*, namely, the set of possible sequences of terminal symbols that can result from repeatedly replacing any nonterminal in the sequence
with a right-hand side of a production for which the nonterminal is the left-hand side.

Grammar Notation
----------------

Terminal symbols are shown in :code:`fixed width` font. Nonterminal symbols are shown in *italic* type.
The definition of a nonterminal is stated by the name of the nonterminal, a colon, and one or more indented
lines representing forms of the nonterminal.

For example:

    *IfThenStatement:*
        *if ( Expression ) Statement*

States that the nonterminal *IfThenStatement* represents:

* The token *if*;

* A *left parenthesis token*;

* An *Expression*;

* A *right parenthesis token*;

* A *Statement*.

In that order.

The syntax *{x}* on the right-hand side of a production denotes zero or more occurrences of *x*.

For example:

    *ArgumentList:*
        *Argument {, Argument}*

States that an *ArgumentList* consists of:

* An *Argument*;

* Zero or more occurrences of a comma and then an *Argument*.

As such, an *ArgumentList* may contain any positive number of arguments.

The syntax *[x]* on the right-hand side of a production denotes zero or one occurrences of *x*,
making *x* an *optional symbol*. As such,

    *BreakStatement:*
        *break [Identifier]*

Is equivalent to:

    *BreakStatement:*
        *break*
        *break Identifier*

The phrase *(one of)* on the right-hand side of a production denotes that each of the symbols on
the following line(s) is an alternative definition. As such,

    *ZeroToThree:*
        *(one of)*
        *0 1 2 3*

Is equivalent to:

    *ZeroToThree:*
        *0
        1
        2
        3*

When an alternative in a production appears to be a token, it represents the sequence of characters
that would make up the token. As such,

    *BooleanLiteral:*
        *(one of)*
        *true false*


Is equivalent to:

    *BooleanLiteral:*
        *t r u e
        f a l s e*

The phrase *but not* on the right-hand side of a production denotes that the following expansions
are excluded from the possible expansion. As such,

    *Identifier:*
        *IdentifierChars but not a Keyword or BooleanLiteral*

Defines an *Identifier* as an *IdentifierChars*, unless those *IdentifierChars* are equivalent to
a token equal to a *Keyword* or a *BooleanLiteral*.

Finally, some nonterminals are defined by a phrase, where it would be impractical to list all of the alternatives.
For example:

    *RawInputCharacter:*
        *any Unicode character*