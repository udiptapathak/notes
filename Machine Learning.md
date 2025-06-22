# Machine Learning

## Statistical Learning Framework

- **Domain Set**, $\mathcal{X}$  
- **Label Set**, $\mathcal{Y}$
- **Training Set**, $S\subseteq\mathcal{X}\times\mathcal{Y}$ 
- **Hypothesis**, $h:\mathcal{X}\rightarrow\mathcal{Y}$
- **Labelling Function**, $f:\mathcal{X}\rightarrow\mathcal{Y}$
- **Probability Distribution**, $\mathcal{D}$ over $\mathcal{X}$
- $\mathbb{P}_{x\sim\mathcal{D}}[f(x)]$ := $\mathbb{P}(\{x\in\mathcal{X}\mid f(x)=\text{True}\}$ where $f:\mathcal{X}\times\{\text{True},\text{False}\}$
- **True Error** $$L_{D,f}(h):=\underset{x\sim\mathcal{D}}{\mathbb{P}}[h(x)\neq f(x)]$$
- **Training Error** $$L_S(h):=\frac{|\{i\in m\mid h(x_i)\neq y_i\}|}{m+1}$$
	where $m=|S|$
- **Overfitting**, $L_{\mathcal{D},f}(h)>>L_S(h)$
- **Hypothesis Class**, $\mathcal{H}$ is a collection of hypothesis
- **Inductive Bias** is to restrict learner to choose a hypothesis from $\mathcal{H}$
- **Empirical Risk Minimization, ERM** is the learning paradigm where $h$ aims to minimize $L_S(h)$ $$\text{ERM}_\mathcal{H}\in\underset{h\in\mathcal{H}}{\text{argmin }} L_S(h)$$
- **Realizability Assumption** $\exists h^\star\in\mathcal{H}\ni L_{\mathcal{D},f}(h^\star)=0$
- **i.i.d assumption**, $S\sim\mathcal{D}^{|S|}$, i.e. each example of $S$ is independently and identically distributed over $\mathcal{D}$.
- **Confidence Parameter**, $1-\delta$ where $\delta$ is the probability of getting a nonrepresentative sample from $\mathcal{D}$
- **Accuracy Parameter**, $\epsilon$ decides quality of hypothesis. $h_S$ is approximately correct if $L_{\mathcal{D},f}(h)\leq\epsilon$
### Bound on Misleading Sample

Let there be a set of bad hypothesis, $\mathcal{H}_B:=\{S\sim\mathcal{D}^m\mid L_{\mathcal{D},f}(h)>\epsilon\}$
Let there be a set of sample where the learner fails, $F:=\{S\sim\mathcal{D}^m\mid h_S\in\mathcal{H}_B\}$
Let there be a set of misleading sample, $M:=\{S\sim\mathcal{D}^m\mid\exists h\in\mathcal{H}_B,L_S(h)=0\}$ 
We want to bound probability of learner failing, $\mathbb{P}(T)$

**Theorem**  $\mathbb{P}(F)\le\mathbb{P}(M)$
**Proof**
$s\in F$
$\implies s\in\{S\sim\mathcal{D}^m\mid h_S\in\mathcal{H}_B\}$
$\implies s\in\{S\sim\mathcal{D}^m\mid h_S\in\mathcal{H}_B, L_S(h_S)=0\}$ (using realizability assumption)
$\implies s\in M$
$\therefore F\subseteq M$
If $h_1,h_2\in M, h_1\ne h_2$, then only one of them will be picked by ERM,
$\therefore M\nsubseteq F$  
$F\subseteq M\implies \mathbb{P}(F)\le\mathbb{P}(M)$
$\square$

**Theorem** $\mathbb{P}(M)\le|\mathcal{H}_B|(1-\epsilon)^m<|\mathcal{H}|e^{-\epsilon m}$
**Proof**
$M:=\{S\sim\mathcal{D}^m\mid\exists h\in\mathcal{H}_B,L_S(h)=0\}=\underset{h\in\mathcal{H}_B}{\bigcup}\{S\sim\mathcal{D}^m\mid L_S(h)=0\}$ 
$\implies\mathbb{P}(M)\le\underset{h\in\mathcal{H}_B}{\sum}\mathbb{P}(\{S\sim\mathcal{D}^m\mid L_S(h)=0\})$
$=\underset{h\in\mathcal{H}_B}{\sum}\left(\underset{i\in m}{\prod}\left(\underset{x_i\sim\mathcal{D}}{\mathbb{P}}[h(x_i)=f(x_i)]\right)\right)$
$=\underset{h\in\mathcal{H}_B}{\sum}\left(\underset{x\sim\mathcal{D}}{\mathbb{P}}[h(x)=f(x)]\right)^m$
$=\underset{h\in\mathcal{H}_B}{\sum}(1-L_{\mathcal{D},f}(h))^m$
$\le\underset{h\in\mathcal{H}_B}{\sum}(1-\epsilon)^m$
$=(1-\epsilon)^m\underset{h\in\mathcal{H}_B}{\sum}1$
$=|\mathcal{H}_B|(1-\epsilon)^m$
$\therefore\mathbb{P}(M)\le|\mathcal{H}_B|(1-\epsilon)^m$
$|\mathcal{H}_B|\le|\mathcal{H}|,(1-\epsilon)^m<e^{-\epsilon m}$
$\implies|\mathcal{H}_B|(1-\epsilon)^m<|\mathcal{H}|e^{-\epsilon m}$
$\square$
## Probably Approximately Correct (PAC) Learning 

A hypothesis class $\mathcal{H}$ is **PAC learnable** if $\exists m_\mathcal{H}(0,1)^2\mapsto\mathbb{N}$, called **sample complexity**, and a learning algorithm $A\ni\forall|S|\ge m_\mathcal{H}(\epsilon,\delta)$ where $S$ is i.i.d by $\mathcal{D}$ and labelled by $f$, $A$ returns a hypothesis $h$ which is probably, with a confidence of $1-\delta$, and approximately, with an error of $\epsilon$, correct. 

$m_\mathcal{H}(\epsilon,\delta)$ is the minimum integer that satisfies the requirement of PAC learning with accuracy of $\epsilon$ and confidence $1-\delta$.

Every finite hypothesis class is PAC learnable with sample complexity $$m_\mathcal{H}(\epsilon,\delta)\le\left\lceil\frac{\mathrm{log}(|\frac{\mathcal{H}}{\delta}|)}\epsilon\right\rceil$$