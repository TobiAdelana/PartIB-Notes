# Compilers

## Definitions

**Compilers** - translates programs in one language with semantics to another language while preserving meaning

Good compilers should:
- Be correct such that meaning is preserved
- Produce usable error messages


### The Semantic Gap
There is a large gap between the higher level languages we write programs in and the lower level target lanuages that are used to execute our code.  

**High level languages**
- Machine independent
- Complex syntax
- Variables
- Nested scopes

**Typical Target**
- Machine specific
- Simple syntax
- Flat scope

## Conceptual view of a typical compiler
![](Compiler_Overview.png)

### Front End
TODO #1


### Middle
- High level to low level translation
- Performs optimisations to code
- Produces a retargetable representation
- There is a tradeoff: if the compiler performs more optimisations; the generated code is fater but the compilation times increase


### Back end
 - Translates low-level retargetable representation to ISA/OS specific code
 - Knows information about target platform
   - Can perform some optimsations based on this information

## Regular Expressions
TODO #2


## Context-Free Grammars
Given $G = (N, T, P, S)$ where
- $N$: set of non-terminals
- $T$: set of terminals
- $P \subseteq N * (N \cup T)^*$: set of productions
- $S \in N$: start symbol

Each production $(A, \alpha) \in P$ is written as $A \rightarrow \alpha$

> ### Example
> $G_1 = (N_1, T_1, P_1, E)$  
> $N_1 = \{E\}$  
> $T_1 = \{+, *, (, ), \text{id}\}$
> 
> $P_1 : E \rightarrow E + E | E * E | (E) | \text{id}$

Given: string of symbols $\alpha A \beta$ and production $A \rightarrow \gamma$, a derivation step is
$$ \alpha A B \Rightarrow \alpha \gamma B$$

### Concrete vs Abstract Syntax Trees

**Concrete Syntax Tree**
- Also known as a parse tree
- This includes a tree defined by terminals and non-terminals
- Includes symbols such as parentheses which are not needed in the abstract Syntax Tree

**Abstract Syntax Tree**
- Only contains information needed to generate the intermediate representation
  
TODO #3

## Pushdown Automata
A finite state automata with a stack included  
Context-free languages are accepted by Pushdown Automata

$M = (Q, \Sigma, \Gamma, \delta, q_0, Z)$  
$Q$: set of states  
$\Sigma$: set of input symbols  
$\Gamma$: set of stack symbols    
$q_0 \in Q$: start state  
$Z \in \Gamma$: initial stack symbol  
$\delta$: transition function for the PDA.  
INPUT: current state, an input symbol and a stack symbol  
OUTPUT: new state, stack symbols
$$\delta: \forall q \in Q, a \in (\Sigma \cup \{\epsilon\}), X \in \Gamma, \delta(q, a, X) \subseteq Q \times \Gamma^*$$

### Instantaneous description
For $q \in Q, w \in \Sigma^*, \alpha \in \Gamma^*$  
$$(q, w, \alpha)$$  
is an instantaneous description. It describes the PDA in state $q$, next input symbol is first input of $w$, first symbol of $\alpha$ is on top of stack

### Language accepted by PDA

For $(q', \beta) \in \delta(q, a, X), a \in \Sigma$  
$(q, aw, X\alpha) \rightarrow (q', w, \beta\alpha)$  

and for $(q', \beta) \in \delta(q, \epsilon, X)$  
$(q, w, X\alpha) \rightarrow (q', w, \beta\alpha)$

### Language Ambiguity
A language is said to be ambiguous if there are multiple left-to-right derivation trees for any string in the language

$x+y*z$ is ambiguous, as $(x+y)*z \neq x+(y*z)$  
Also, $x+y+z$ is ambiguous even if $(x+y) +z \equiv x + (y+z)$ as they have different parse trees.
TODO #4

Semantic ambiguity causes problems as we transition from program texts to derivation trees as it produces nondeterministic results.
