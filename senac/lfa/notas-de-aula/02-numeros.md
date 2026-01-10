# Notas de aula — Conjuntos numéricos, tamanhos e computabilidade 📝

> Convenção: vou usar $\mathbb{N}=\{0,1,2,\dots\}$. Em alguns livros aparece $\mathbb{N}=\{1,2,3,\dots\}$; quando isso importar, eu aviso.

Mapa rápido de inclusões (para situar):
$$\mathbb{N}\subset\mathbb{Z}\subset\mathbb{Q}\subset\mathbb{R}.$$

---

**1) Definição — Números Naturais ($\mathbb{N}$)**

Ideia: números para *contar* (quantidades inteiras não negativas).

Definição:
$$\mathbb{N}=\{0,1,2,3,\dots\}.$$

Observações úteis:
- $\mathbb{N}$ é fechado para soma e produto: se $a,b\in\mathbb{N}$, então $a+b\in\mathbb{N}$ e $ab\in\mathbb{N}$.
- Não é fechado para subtração: por exemplo, $1-2=-1\notin\mathbb{N}$.

---

**2) Definição — Números Reais ($\mathbb{R}$) e a divisão em Racionais e Irracionais**

Ideia: os reais são os números que “moram” na reta numérica (incluindo inteiros, frações e números como $\sqrt{2}$ e $\pi$).

Definição (racionais):
$$\mathbb{Q}=\left\{\frac{p}{q}\,:\,p,q\in\mathbb{Z},\ q\neq 0\right\}.$$

- Em decimal, racionais são exatamente os que têm **expansão finita** (ex.: $2{,}75$) ou **periódica** (ex.: $0{,}333\dots$).

Definição (irracionais):
$$\mathbb{R}\setminus\mathbb{Q}=\{x\in\mathbb{R}:x\notin\mathbb{Q}\}.$$

- Em decimal, irracionais têm expansão **infinita e não-periódica** (ex.: $\sqrt{2}=1{,}414213\dots$).

Partição dos reais:
$$\mathbb{R}=\mathbb{Q}\ \cup\ (\mathbb{R}\setminus\mathbb{Q})\quad\text{e}\quad \mathbb{Q}\cap(\mathbb{R}\setminus\mathbb{Q})=\varnothing.$$

---

**3) Por que o conjunto dos Reais é “maior” do que o dos Naturais (Cantor)** ⭐

Para comparar tamanhos de conjuntos infinitos, Cantor propôs comparar por **bjeções** (correspondências perfeitas).

Definição (conjunto contável):
$$A\ \text{é contável se existe uma bijeção}\ f:\mathbb{N}\to A.$$

- $\mathbb{N}$ é contável (trivialmente).
- Também $\mathbb{Z}$ e $\mathbb{Q}$ são contáveis (existem listagens que passam por todos eles sem faltar nenhum).

A grande virada de Cantor: **$\mathbb{R}$ não é contável** (é *incontável*). A prova clássica usa o *argumento diagonal*.

**Esboço do argumento diagonal (em $(0,1)$):**
1. Suponha, para obter contradição, que dá para listar todos os reais de $(0,1)$:
   $$x_1,\ x_2,\ x_3,\ \dots$$
2. Escreva cada $x_n$ em decimal. Por exemplo:
   - $x_1 = 0,a_{11}a_{12}a_{13}\dots$
   - $x_2 = 0,a_{21}a_{22}a_{23}\dots$
   - $x_3 = 0,a_{31}a_{32}a_{33}\dots$
3. Construa um novo número $y=0,b_1b_2b_3\dots$ escolhendo cada dígito $b_n$ diferente do dígito diagonal $a_{nn}$ (por exemplo, escolha $b_n=1$ se $a_{nn}\neq 1$, e $b_n=2$ se $a_{nn}=1$; assim evitamos o dígito 9 e também ambiguidades do tipo $0{,}4999\dots=0{,}5$).
4. Então $y$ difere de $x_1$ no 1º dígito, difere de $x_2$ no 2º dígito, etc. Logo, $y$ **não é igual a nenhum** $x_n$.
5. Contradição: a lista não podia conter “todos” os reais de $(0,1)$.

Conclusão:
- $(0,1)$ é incontável.
- Como $(0,1)\subset\mathbb{R}$, o conjunto $\mathbb{R}$ também é incontável.

Um jeito padrão de registrar isso em cardinalidades:
$$|\mathbb{N}|=\aleph_0 \quad\text{e}\quad |\mathbb{R}|=2^{\aleph_0}.$$

---

**4) Irracionais: Algébricos e Transcendentais (e o tamanho desses conjuntos)**

Os irracionais se dividem em dois grandes tipos: **algébricos** e **transcendentais**.

Definição (número algébrico):
$$x\in\mathbb{R}\ \text{é algébrico se existe}\ P\in\mathbb{Z}[t]\setminus\{0\}\ \text{com}\ P(x)=0.$$

Exemplos:
- $\sqrt{2}$ é algébrico porque satisfaz $t^2-2=0$.
- Todo racional é algébrico: se $x=\frac{p}{q}$, então $qx-p=0$.

Definição (número transcendental):
$$x\in\mathbb{R}\ \text{é transcendental se não é algébrico.}$$

Exemplos famosos (não triviais): $\pi$ e $e$ são transcendentais.

**Tamanho (cardinalidade) dos conjuntos:**
- O conjunto dos polinômios com coeficientes inteiros é contável (dá para listar todas as sequências finitas de inteiros).
- Cada polinômio não nulo tem **número finito** de raízes reais.
- A união contável de conjuntos finitos é contável.

Logo:
$$\{\text{números algébricos}\}\ \text{é contável.}$$

Como $\mathbb{R}$ é incontável, sobra “muito mais” coisa fora dos algébricos; portanto:
$$\{\text{números transcendentais}\}\ \text{é incontável.}$$

Consequência intuitiva:
- Embora seja difícil “apontar” transcendentais específicos, **a maioria dos reais** (em termos de tamanho do conjunto) é transcendental.

---

**5) Números computáveis e não-computáveis (sem Máquina de Turing)** 🔹

Ideia: um real é **computável** se existe um procedimento (um algoritmo) que consegue gerar aproximações cada vez melhores, com garantia de erro.

Definição (real computável):
$$x\in\mathbb{R}\ \text{é computável se existe um algoritmo que, dado}\ n,\ \text{produz}\ q_n\in\mathbb{Q}\ \text{com}\ |x-q_n|\le 2^{-n}.$$

- Interpretando: com a entrada $n$, o algoritmo devolve uma fração $q_n$ que aproxima $x$ com erro no máximo $2^{-n}$.

Exemplos de computáveis:
- Todo racional (é fácil aproximar exatamente).
- $\sqrt{2}$ (por bisseção ou outros métodos numéricos para resolver $t^2=2$).
- $\pi$ e $e$ (por séries, limites e algoritmos clássicos).

Definição (real não-computável):
$$x\in\mathbb{R}\ \text{é não-computável se não existe algoritmo que produza essas aproximações com erro garantido para todo}\ n.$$


**Tamanho do conjunto dos computáveis vs. não-computáveis**
- Algoritmos podem ser descritos por textos finitos (códigos/receitas finitas).
- Existe apenas uma quantidade contável de descrições finitas.
- Cada algoritmo descreve no máximo um real computável.

Logo:
$$\{\text{reais computáveis}\}\ \text{é contável.}$$

Como $\mathbb{R}$ é incontável, segue imediatamente:
$$\{\text{reais não-computáveis}\}\ \text{é incontável.}$$

**Relação com algébricos e transcendentais**
- Todo algébrico é computável (há métodos gerais para aproximar raízes de polinômios com precisão arbitrária).
- Existem transcendentais computáveis (como $\pi$ e $e$).
- Como os computáveis são contáveis e os transcendentais são incontáveis, “sobram” transcendentais demais: a maioria dos transcendentais é não-computável.

Resumo das inclusões relevantes:
$$\{\text{algébricos}\}\subset\{\text{computáveis}\}\subset\mathbb{R}.$$
$$\{\text{não-computáveis}\}\subset\{\text{transcendentais}\}\subset(\mathbb{R}\setminus\mathbb{Q}).$$

---

**6) O que é um número definível (e como ele se compara aos computáveis)**

Ideia: um número é **definível** se existe uma descrição finita (uma propriedade bem especificada) que o identifica unicamente.

Definição (real definível):
$$x\in\mathbb{R}\ \text{é definível se existe uma descrição finita}\ P(\cdot)\ \text{tal que existe exatamente um real}\ r\ \text{com}\ P(r)\ \text{verdadeira.}$$

Exemplos intuitivos:
- $0$ é definível (“o único real neutro da soma”).
- $\sqrt{2}$ é definível (“o único real positivo cujo quadrado é 2”).
- $\pi$ é definível (por propriedades geométricas ou analíticas).

**Tamanho do conjunto dos definíveis**
- “Descrições finitas” também formam um conjunto contável (há contavelmente muitos textos finitos).

Logo:
$$\{\text{reais definíveis}\}\ \text{é contável.}$$

Comparação com computáveis:
- Todo computável é definível (basta definir o número como “o limite”/“o valor” produzido por um procedimento especificado).
- Mas nem todo definível precisa ser computável.

Em termos de inclusão:
$$\{\text{computáveis}\}\subset\{\text{definíveis}\}\subset\mathbb{R}.$$

> Observação (sutil): “definível” depende do *idioma matemático* e das regras/axiomas que você aceita. Para notas de aula, a intuição de “ter uma descrição finita que aponta unicamente o número” é o ponto principal.

---

**Resumo final (tamanhos)**
- Contáveis: $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{Q}$, algébricos, computáveis, definíveis.
- Incontáveis: $\mathbb{R}$, irracionais, transcendentais, não-computáveis.
