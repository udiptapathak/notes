# Formal Logic

###### Definitions

- **Statement** is regarded as the information content of an information bearing statement.
- **Propositions** are indicator functions that take a world and returns a truth value.
- **Reasoning** is transforming the information present in a set of premises to reach a conclusion.
- **Inferences** are steps in reasoning moving from premises to conclusion.
- **Logic** is the study of correct reasoning.
- **Formal Logic** uses formal system to study reasoning.
### Structural Induction

Let $U$ be a set, $B\subseteq U$ an initial set, and $\mathcal{F}$ a class of functions $\{f:U^n\rightarrow U, \text{ for some }n\in\mathbb{N}\}$  

We wish to construct a set $C$ containing elements that can be constructed by applying functions from $\mathcal{F}$ composed on elements from $B$

#### Top Down Approach

Set $S$ is inductive if $B\subseteq S$ and $S$ is closed under $\mathcal{F}$ .

$$C^\star=\bigcup\{S\in\mathcal{P}(U)\mid S\text{ is inductive}\}$$
#### Bottom Up Approach

1. Let $C_0=B$
2. Let $C_i=f(x\in C^n_{i - 1})\text{ for some }f\in\mathcal{F}$
$$C_\star=\bigcup_{n\in\mathbb{N}} C_n$$
#### Induction Principle

$C^\star=C_\star$ and it is our desired set $C$, the set *generated from* $B$ by the functions in $\mathcal{F}$.

If $C$ is a set generated from $B$ by the functions in $\mathcal{F}$ and $S$ is a subset of $C$ that includes $B$ and is
closed under the functions of $\mathcal{F}$ then $S=C$.

### Transfinite Recursion Theorem


## Sentential Logic 

### Language

All symbols are distinct and no symbols is a finite sequence of other symbols.

- **Sentential Connective Symbol**  $\neg,\land,\lor,\rightarrow,\leftrightarrow$
- **Logical Symbol** $\{\text{Sentential Connective Symbol}\}\cup\{\text{Parenthesis}\}$
- **Sentence Symbol/Proposition Symbol** $A_{i\in\mathbb{N}}$
- **Expression** Finite sequence of symbols
- **Well Formed Formula**
	- Every sentence symbol is $\mathrm{wff}$
	- If $\alpha$ and $\beta$ are $\mathrm{wff}$, then so are $(\neg\alpha),(\alpha\land\beta),(\alpha\lor\beta),(\alpha\rightarrow\beta),(\alpha\leftrightarrow\beta)$
	
### Interpretation	

- *Truth assignment* or *model* $v$ for a set $S$ of sentence symbols is a function $v:S\rightarrow\{T,F\}$
- A model $v$ *satisfies* $\phi$ $\mathrm{iff}$ $\overline{v}(\phi)=T$
- A set of $\textrm{wff},\Sigma$ *tautologically implies* a $\mathrm{wff},\tau$ (written as $\Sigma\models\tau$) $\mathrm{iff}$ every model that satisfies every member of $\Sigma$ also satisfies $\tau$
- $\varnothing\models\tau$ $\mathrm{iff}$ every truth assignment satisfies $\tau$. $\tau$ in this case is called a *tautology* (written as $\models\tau$) 
- If $B_\alpha$ is a boolean function realized by $\mathrm{wff}$ $\alpha$, and $F<T$, then $\alpha\models\beta$ $\mathrm{iff}$ $\forall\vec{X}\in\{F,T\}^n,B_\alpha(\vec{X})\le B_\beta(\vec{X})$
- 0-ary connectives - $\bot=\{(,F)\}$ and $\top=\{(,T)\}$
- A set of sentential connective, $X$ is *complete* if $\forall G:\{F,T\}^n\mapsto\{F,T\},\exists \alpha\ni G=B_\alpha$, where $\alpha$ is a $\mathrm{wff}$ constructed using the sentential connective in $X$.
- $\{\neg,\land\},\{\neg,\lor\},\{\neg,\rightarrow\},\{\mathrm{nand}\},\{\mathrm{nor}\}$ are complete.
- $\{\bot,\rightarrow\}$ is *supercomplete* because it can also realize $G:\varnothing\mapsto\{F,T\}$ .

### Compactness and Effectiveness

- **Compactness Theorem**: Let $\Sigma$ be a set of $\textrm{wff}$s $\ni\forall\text{ finite }\Sigma_0\in\Sigma$, there is a model that satisfies every member of $\Sigma_0$, then there is a model that satisfies every member of $\Sigma$. 
- An **effective procedure** must 
	- Be a program of finite instructions
	- Run on an automata
	- Halt for a decision problem
- A language $\Sigma$ is **decidable** if an effective procedure can decide if $\alpha\in\Sigma$.
- The language of sentential logic is decidable.
- A language $\Sigma$ is **effectively enumerable** if an effective procedure can list all its member in some order.
- A language $\Sigma$ is **semidecidable** if an effective procedure returns $T$ only if $\alpha\in\Sigma$.
- A language is effectively enumerable $\mathrm{iff}$ it is semidecidable.
## First Order Logic

### Language

All symbols are distinct and no symbols is a finite sequence of other symbols.

- **Sentential Connective Symbol**  $\neg,\land,\lor,\rightarrow,\leftrightarrow$
- Variables $v_{i\in\mathbb{N}}$
- **Logical Symbol** $\{\text{Sentential Connective Symbol}\}\cup\{\text{Parenthesis}\}\cup\{\textnormal{Variables}\}\cup\{=\}^+$
- **Quantifier Symbol** $\forall$
- **Predicate Symbol** $n$-place predicate symbol shows relation between $n$ elements.
- **Function Symbol** $n$-ary function symbol returns a single element.
- **Constant Symbol** $0$-ary function symbol.
- **Terms** are variables and expressions formed by applying function symbol to variables.
- **Atomic Formula** are expressions formed by applying predicate symbol to terms.
- **Well Formed Formula** are expression formed by applying 0 or more logical symbol on atomic formulas.
- **Free Variable**
	- For atomic $\alpha$, $x$ occurs free in $\alpha$ $\mathrm{iff}$ $x$ occurs in $\alpha$  
	- $x$ occurs free in $\neg\alpha$ $\mathrm{iff}$ $x$ occurs free in $\alpha$
	- $x$ occurs free in $\alpha\rightarrow\beta$ $\mathrm{iff}$ $x$ occurs free in $\alpha$ or in $\beta$
	- $x$ occurs free in $\forall v_i\alpha$ $\mathrm{iff}$ $x$ occurs free in $\alpha\land x\ne v_i$
- **Sentence** is a $\mathrm{wff}$ with no free variables.

### Interpretation

#### Structure

A **structure** $\mathfrak{A}$  for our FOL is a function that maps each

- $\forall$ a non empty set $|\mathfrak{A}|$ called universe or domain of $\mathfrak{A}$.
- $n$-place predicate symbol $P$ an $n$-ary relation $P^\mathfrak{A}\subseteq|\mathfrak{A}|^n$
- $n$-place function symbol $f$ an $n$-ary operation $f^\mathfrak{A}:|\mathfrak{A}|^n\rightarrow|\mathfrak{A}|$

Let $\mathfrak{A},\mathfrak{B}$ be structures for our language. A function $h:\mathfrak{A}\mapsto\mathfrak{B}$ is a *homomorphism* if
- $\langle a_1,\ldots,a_n\rangle\in P^\mathfrak{A}\leftrightarrow\langle h(a_1),\ldots,h(a_n)\rangle\in P^\mathfrak{B}$
- $h(f^\mathfrak{A}(a_1,\ldots,a_n))=f^\mathfrak{B}(h(a_1),\ldots,h(a_n))$

If $h$ is injective, then it is called an *isomorphism*.
#### Model

Let $s:V\rightarrow|\mathfrak{A}|$ then $\mathfrak{A}$ *satisfies* a $\mathrm{wff}$ $\varphi$ with $s$, $\models_\mathfrak{A}\varphi[s]$ 
- If for terms $T$, we can extend $s$ to $\overline{s}:T\rightarrow|\mathfrak{A}|\ni$ for each
	- variable $x$, $\overline{s}(x)=s(x)$
	- $n$-place function $f$, if $t_1\ldots t_n$ are its argument, then $\overline{s}(f(t_1,\ldots,t_n)=f^\mathfrak{A}(\overline{s}(t_1),\ldots,\overline{s}(t_n))$
- If for atomic formulas
	- $\models_{\mathfrak{A}}=t_1t_2[s]$ $\mathrm{iff}$ $\overline{s}(t_1)=\overline{s}(t_2)$
	- For an $n$-place predicate $P, \models_\mathfrak{A}P(t_1,\ldots,t_n)[s]$ $\mathrm{iff}$ $\langle\overline{s}(t_1),\ldots,\overline{s}(t_n)\rangle\in P^\mathfrak{A}$
- If for other $\mathrm{wff}$
	- $\models_\mathfrak{A}\neg\varphi[s]$ $\mathrm{iff}$ $\nvDash_\mathfrak{A}\varphi[s]$
	- $\models_\mathfrak{A}\varphi\rightarrow\psi$ $\mathrm{iff}$ $\nvDash_\mathfrak{A}\varphi[s]\lor\models_\mathfrak{A}\psi[s]$ 
	- $\models_\mathfrak{A}\forall x\psi[x]$ $\mathrm{iff}$ $\forall d\in|\mathfrak{A}|,\models_\mathfrak{A}\varphi[s(x|d)]$
	where $s(x|d)(y)=\begin{cases}s(y)&\text{if }y\ne x\\d&\text{if }y=x\end{cases}$

**Theorems and Definitions**

- If $s_1,s_2:V\mapsto|\mathfrak{A}|$ agrees on all free variables in $\mathrm{wff}$ $\varphi$ then $\models_\mathfrak{A}\varphi[s_1]\leftrightarrow\models_\mathfrak{A}\varphi[s_2]$
- Let there a be a set of $\mathrm{wff}$ $\Gamma$ *logically implies* $\varphi$, $\Gamma\models\varphi$ $\mathrm{iff}$ $\forall\mathfrak{A}$ for the language and $\forall s:V\mapsto|\mathfrak{A}|$ that satisfies every member of $\Gamma$ also satisfied $\varphi$ with $s$.
- A set $\{\langle a_1,\ldots,a_k\rangle\mid\models_\mathfrak{A}\varphi[[a_1,\ldots,a_k]]\}$ is said to be *definable* in $\mathfrak{A}$.
- $\text{Mod }\Sigma$ is the class of all mx 7odels that satisfies all the members of the set of sentences, $\Sigma$.
- A class $\mathcal{K}$ is an *elementary class* ($\mathrm{EC_\triangle}$)  if $\exists\Sigma\ni\mathcal{K}=\text{Mod }\Sigma$.

