# Linear Algebra

## Vector Spaces 

### Fields

**Axioms of Addition**
1. $x+y=y+x$
2. $x+(y+z)=(x+y)+z$
3. $\exists\ 0\ni x+0=x$
4. $\exists\ -x\ni x+(-x)=0$

**Axiom of Multiplication**
1. $xy=yx$
2. $x(yz)=(xy)z$
3. $\exists\ 1\ni x1 = x$
4. $\forall x\ne0\ \exists x^{-1}\ni xx^{-1}=1$
5. $x(y + z)=xy+xz$

### Vector Space

A vector space has a field $F$ of scalars and a set $V$ of vectors satisfying following axioms

**Axioms of Vectors Addition**
1. $\alpha+\beta=\beta+\alpha$
2. $\alpha+(\beta+\gamma)=(\alpha+\beta)+\gamma$
3. $\exists\,0\in V\ni\alpha+0=\alpha$
4. $\forall\,\alpha\,:\,\exists\,-\alpha\ni\alpha+(-\alpha)=0$

**Axioms of Scalar Multiplication**
1. $\forall\,\alpha\in V\,:\,1\alpha=\alpha$ 
2. $(c_1c_2)\alpha=c_1(c_2\alpha)$
3. $c(\alpha+\beta)=c\alpha+c\beta$
4. $(c_1+c_2)\alpha=c_1\alpha+c_2\alpha$

- A vector $\beta$ is *linear combination* of $\{\alpha_{i\in n}\}$ if $\exists\,\langle c_{i\in n}\rangle\ni\beta=\sum^n_{i=1}c_i\alpha_i$
-  A set $W\subseteq V$ is a *subspace* of vector space $V$ if $W$ is a vector space over $F$ with closed vector addition and scalar multiplication.
- Intersection of any collection of subspaces of $V$ is a subspace in $V$.
- A subspace *spanned* by a set of vector $S$ in $V$ is set of all linear combinations of vectors in $S$. This subspace is also equal to the intersection of all subspaces of $V$ containing $S$. 
- $S=\{\alpha_{i\in n}\}\subseteq V$ is linearly independent if $\forall\,\langle c_{i\in n}\rangle\,:\,\langle c_{i\in n}\rangle=\langle0,\ldots,0\rangle\,\longleftrightarrow\,\sum_{i\in n}c_i\alpha_i=0$ 
- *Basis* for $V$ is a linearly independent set of vectors that spans $V$.
- *Dimension*, $\mathrm{dim}\,V$ is the size of basis for $V$. Any basis for $V$ will have same dimension and any independent set of vectors in $V$ cannot have a size more than $\mathrm{dim}\,V$. 
- *Ordered Basis* is a basis with total order defined on it. If $\langle\alpha_{i\in n}\rangle$ is an ordered basis, then $\forall\beta\in V\,:\,\exists\langle c_{i\in n}\rangle\,\ni\,\beta=\sum_{i\in n}c_i\alpha_i$. The tuple $\langle c_{i\in n}\rangle$ is called *coordinate* of $\beta$ w.r.t. that order basis.
### Matrices and Row Operation

**Elementary Row Operations**
1. Row switching: $R_i\leftrightarrow R_j$
2. Row multiplication: $R_i\rightarrow cR_i$
3. Row addition: $R_i\rightarrow R_i+cR_j$

- All elementary row operations are invertible. $A$ and $B$ are *row equivalent* if $A$ can be obtained from $B$ with finite elementary row operations and $AX=0$ and $BX=0$ has same set of solutions.
- $A$ is in *row reduced form* if
	1. First non-zero entry in each row is 1.
	2. If $a_{ij}$ is the first non-zero entry of $R_i$ then $\forall\ k\ne j\ a_{ik}=0$
- $A$ is in *row reduced echelon form* if	
	1. It is in row reduced form
	2. Rows with all zero entries come after rows with non zero entries
	3. If first non zero entry of each non zero row $i$ is $k_i$, then $i<j\longleftrightarrow k_i< k_j$
- Every $A$ is reducible to row equivalent to a row reduced echelon form. All row equivalent matrices has the same row reduced echelon matrix.
- $C=AB\coloneqq C_{ij}=\sum^n_{r=1}A_{ir}B_{rj}$
- We can consider $A_{m\times n}$ a collection of row vectors $\langle \alpha_{i\in m}\rangle$. *Row space* is the subspace of $F^n$ spanned by these vectors. *Row Rank* is the dimension of this row space.
- Row equivalent matrices have the same row space. The non zero rows in row reduced echelon form constructs one basis for its row space. 
## Linear Transformation

- A linear transformation, $T:V\mapsto W$ is a function that satisfies $T(c\alpha+\beta)=c(T\alpha)+T\beta$
- *Null space* of $T$ is the set $\{\alpha\in V\mid T\alpha=0\}$
- *Rank* of $T$ is $\mathrm{dim}\;(\mathrm{rng}\;T)$ and *nullity* of $T$ is the dimension of its null space.
- $\mathrm{rank}\;T+\mathrm{nullity}\;T=\mathrm{dim}\;T$