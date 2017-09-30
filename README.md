# DFALang
An interpreter of a simple language for working with Deterministic Finite Automata.

### Introduction
The language has a simple structure. It allows you to define Deterministic Finite Automata and ask to accept strings by them.

An automaton *definition* in this language looks like this:

```
DFA A1 {
  S = 4
  A = {a, b, c}
  T = {(1,a,2), (1,b,3), (2,c,4), (3,b,1)}
  F = {2, 4}
}
```
Ask to *accept a string* with this automaton: <br />
```
Accept "abc" with A1
```
You can also ask to *accept a string with several automata* at the same time:  <br />
```
Accept "abc" with {A1, A2, A3}
```
<br />

### The language grammar. <br />

```
Program        = {[NewLines] Module}.
Module         = (DefModule | AcceptModule) NewLines.
DefModule      = 'DFA' ID '{' States Alphabet Transitions FinalStates '}'.
AcceptModule   = 'Accept' STRING 'with' IDList.
States         = 'States'|'S' '=' NUMBER.
Alphabet       = 'Alphabet'|'A' '=' LetterList.
Transitions    = 'Transitions'|'T' '=' TransitionList.
FinalStates    = 'FinalStates'|'F' '=' NumberList.
LetterList     = '{' LETTER {',' LETTER} '}'.
NumberList     = '{' NUMBER {',' NUMBER} '}'.
IDList         = '{' ID {',' ID} '}'.
TransitionList = '{' Transition {',' Transition} '}'.
Transition     = '(' NUMBER ',' LETTER ',' NUMBER ')'.
NewLines       = NL {NL}.
```
