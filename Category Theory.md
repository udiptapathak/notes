# Category Theory

A category $\mathcal{C}$ consists of:
- A class $\text{ob}(\mathcal{C}$) of *objects*
- A class $\text{hom}(C)$  of *morphisms*. Each morphism $f$ has a *source object* $a$ and *target object* $b$
	- $f:a\mapsto b$	is a morphism $f$ from $a$ to $b$ 
	- $\text{hom}_\mathcal{C}(a,b)$ or $\mathcal{C}(a,b)$ is a *hom-class* of all morphisms from $a$ to $b$
- Composition of morphism $\circ:\text{hom}(b,c)\times\text{hom}(a,b)\mapsto\text{hom}(a,c)$
	Composition of $f:a\mapsto b$ and $g:b\mapsto c$ is written as $g\circ f$
	The composition has following axioms:
	- Associativity: $h\circ(g\circ f)=(h\circ g)\circ f$
	- Identity: $\forall x\in\text{ob}(\mathcal{C})\exists 1_x:x\mapsto x\ni\forall f:a\mapsto b\in\text{hom}(\mathcal{C}): 1_b\circ f = f = f \circ 1_a$ 
	