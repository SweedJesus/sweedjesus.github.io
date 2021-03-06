---
layout: default
title: 'Music theory'
anchor: true
math: true
toc: true
---

<!-- VexFlow -->
<script type='text/javascript' src='https://unpkg.com/vexflow/releases/vexflow-min.js'></script>
<script type='text/javascript' src='front.js'></script>

<div class='vf helper' data='random-3-2'></div>

# Abstract Algebra and Modular arithmetic

<div class='vf simple-score'
    {% capture music %}
F4q F4q | R4qr Ab4q | Ab4q G3q | G3q F#4q | R48r Bb3qd |
E4qd R48r | C5q C#4q | C#4q D5q | D5q R4qr | B4q B4q
    {% endcapture %}
    params='{ "width": 860 }'
    music='{{ music }}'>
</div>

Analyzing post-tonal or atonal music is a far-cry from classical musical analysis of functional
harmony. The jargon we have become so use to---tonic chords, dominant chords, tonicization,
modulation, etc.---are gone, and in their place we are left with numbers, sets, and transformations.
In most ways the transition to post-tonal analysis purely mathematical, which to many is a scary
transition, but as I am a student of mathematics in additional to music, I wont shy away from the
math that sitting in the background.

Before discussing anything about music, I think it is more than appropriate to familiarize
ourselves with this math that will be in the background of all of post-tonal analysis, in particular
modular arithmetic, a subject in abstract algebra. Fortunately, following this math setup
everything will be simplified notationally.

We're only going to try to understand what is meant by the following:

- “$a$ is congruent/equivalent to $b$ modulo $n$”,
- “$[a]_n$ is the congruence class of $a$ modulo $n$.”

<!--
   -{% thm %}
   -If math *really* isn't of interest to you then feel free to skip this section and instead head
   -straight to [pitch class](#pitch-class), but know that most atonal music techniques are built upon
   -the notion of modular arithmetic, which this section will briefly build up.
   -{% endthm %}
   -->
{% thm %}
Whenever I set text with a gray border to the left, like this, I'll either be summarizing some
mathematical notation and what it means, or going deeper into some of the math previously
introduced.
{% endthm %}

## Quotient-remainder theorem

Chances are you know about Euclidean division.
For example, $1\div 2$ is 1 divided by 2 (or 2 dividing 1) and represents symbolically the number of
times 2 goes into 1 plus some remainder.
What might not be as familiar are the two parts of Euclidean division taken separately:
the *quotient* and the *remainder*.

Let $a$ and $b$ both be integers.

- The quotient $q$ of $a\div b$ is the number of multiples of $b$ that go into $a$, and
- The remainder $r$ of $a\div b$ is what ever is left from subtracting $qb$ from $a$.

And can express $a$ as the sum:

$$
a = qb + r.
$$

{% thm %}
As an aside on notation, mathematicians are often lazy. The "let" statement above could be
alternatively expressed "fix $a,b\in\Z$", where the symbol $\in$ means that $a$ and $b$ are
variables with values taken from $\Z$, where $\Z=\\{\ldots,-2,-1,0,1,2,\ldots\\}$ is the set
containing all integers.

The $\\{\ldots\\}$ notation is called set-builder notation, and is a way to group things, in this case
integers, without repetition. A set can be finite or infinite, for example: $\\{0,1,2\\}$ is a finite
set containing only the integers 0, 1 and 2; $\\{1,2,3,\ldots\\}$ is an infinite set containing all of
the positive integers, commonly denoted $\Z^+$ or $\N$. We can also define sets using rules, as for
example the positive integers can also be expressed as $\\{d\in\Z:d>0\\}$, meaning the set of any
integer $d$ as long as $d$ is greater than zero.

Also to note is the *without repetition* part, meaning sets expressed as containing multiple of the
same element (multiple, not multiples of!) can be reduced to include it only once, e.g.:
$\\{1,1\\}=\\{1\\}$.
{% endthm %}

Here's a few example of quotient-remainder theorem when $b=12$ for a few different values of $a$:

- If $a=12$, then $12=(1)12+(0)$.
- If $a=1$, then $1=(0)12+(1)$.
- If $a=-5$, then $-5=(0)12+(-5)=(-1)12+(7)$.

## Modular congruence and congruence classes

With the last of the examples above you might notice that there were written two different ways to
express -5 as a sum of a multiple of 12 and a remainder. But these aren't the only ways, in-fact
there is an infinite number of ways to express -5 using quotient remainder theorem since for any
arbitrary quotient $q$ there is a unique remainder $r$ such that $a=qb+r$:

$$
\begin{alignedat}{3}
    -5 &= & (-2)12 &+ & ( 19)& \\
    -5 &= & (-1)12 &+ &   (7)& \\
    -5 &= &  (0)12 &+ &  (-5)& \\
    -5 &= &  (1)12 &+ & (-17)& \\
    -5 &= &  (2)12 &+ & (-29)&
\end{alignedat}
$$

What we're getting at is that these remainders are all equal to -5 when we add some multiple of 12,
and we call these remainders *congruent/equivalent* to one-another *modulo 12*.

{% thm d Congruence/equivalence %}
Fix $a$, $b$ and $n$ all be integers where $a$ and $b$ are congruent modulo $n$.
We express this congruence:

$$
a\equiv b\bmod n.
$$
{% endthm %}

{% thm %}
The $\equiv$ symbol means equivalence/congruence and is not the same as equality. For example, -5
and 7 are not equal to one-another, but they are congruent to one-another modulo 12:

$$
-5 \ne 7 \text{, but } -5 \equiv 7\bmod 12.
$$

Also note that whenever we "fix" variables, they are completely new meanings to the variables, and
no other variables are assumed to exist. In the definition of congruence, the variables $a$ and
$b$ are unrelated to the $a$ and $b$ used in the definition of the quotient-remainder theorem.
{% endthm %}

Here are a couple examples of modular equivalence over the divisor $2$:

- $0 \equiv 0 \bmod 2$ since $2$ divides $1$ zero times with a remainder of $0$,
- $1 \equiv 1 \bmod 2$ since $2$ divides $1$ zero times with a remainder of $1$,
- $2 \equiv 0 \bmod 2$ since $2$ divides $2$ once with a remainder of $0$,
- $3 \equiv 1 \bmod 2$ since $2$ divides $2$ once with a remainder of $1$.

And here are a couple examples of modular equivalence over the divisor $12$:

- $11 \equiv 11 \bmod 12$ since $12$ divides $11$ zero times with a remainder of $11$,
- $12 \equiv 0 \bmod 12$ since $12$ divides $12$ once with a remainder of $0$,
- $13 \equiv 1 \bmod 12$ since $12$ divides $12$ once with a remainder of $1$.

In the example with $-5=(0)12+(-5)=(-1)12+(7)$ we saw that there is an infinite amount of
remainders congruent to $7 \bmod 12$. Instead of listing them out (which might take a while, since
there's an infinite number of them), we call this set of congruent integers the *congruence class*
of 5 modulo 12, and denote it:

$$
[5]_{12} = \{\ldots,19,7,-5,-17,-29,\ldots\}.
$$

{% thm d Congruence class %}
Fix an integer $a$, and another integer $n$ the divisor.
We call $[a]_n$ the congruence class of $a$ modulo $n$, and denote it:

$$
[a]_n
= \{\ldots,-1\cdot n+a,0\cdot n+a,1\cdot n+a,\ldots\}
= \{b:b\equiv a\bmod n\}.
$$
{% endthm %}

What is important to see though is that there is a finite number of congruence classes with respect
to equivalence. For example, when 12 is our divisor, there's exactly 12 distinct congruence classes:

$$
[0]_{12},[1]_{12},\ldots,[10]_{12},[11]_{12}.
$$

And while there are an infinite number of ways to denote congruence classes:

$$
\begin{gathered}
\ldots = [-12]_{12} = [0]_{12} = [12]_{12} = [24]_{12} = \ldots \\
\ldots = [-11]_{12} = [1]_{12} = [13]_{12} = [25]_{12} = \ldots \\
\ldots = [-10]_{12} = [2]_{12} = [14]_{12} = [26]_{12} = \ldots \\
\vdots
\end{gathered}
$$

We stick with the *canonical* representations of them: $[a]_n$ where $0\le a < n$.

{% thm %}
As a bonus, $\Z_n$ is the set of congruence classes of integers modulo $n$, which is a finite
set, with respect to equivalence, of $n$ elements where every element is itself an infinite set:

$$
\Z_n = \{[0]_n,[1]_n,[2]_n,\ldots,[n-1]_n\} = \{[a]_n:0\le a\lt n\}.
$$

Math is neat 🤯
{% endthm %}

But how does modular arithmetic relate to music?

---

# Atonal-Theory

## Pitch classes

If you are familiar with music, then you know that there are 12 distinct pitches, each with various
octaves. For example, middle C lies at the center of a piano and is also the note called C4, and C3
and C5 lie one octave below and above C4 respectively. However several notes may be indistinct to
one-another, that is they are *enharmonic*. For example the notes D-sharp 2 and E-flat 2 are
enharmonic.

If you are familiar with music theory, then you also know that a C-major chord is called a C-major
chord regardless of what octave of C it is built upon. Nevertheless octaves of the same pitch are
still distinct; C4 and C5 are different notes on the keyboard or on a music staff, just as 0 is not
equal to 12.

<div class='vf helper' data='C4/q,C5'></div>

On the other hand, different octaves of C are *equivalent* to one-another in that they are all C.

{% thm d Pitch class %}
A pitch class is a collection of pitches related by an integer multiple of an octave and/or
enharmonic equivalence.
{% endthm %}

With this definition we can draw a relation between music and modular arithmetic by associating each
pitch class with a congruence class over the integers modulus 12. But since, as far as music is
concerned, we will always be working over the integers modulus 12. Thus we can simplify notation
going forward by writing $0$ instead of $[0]\_{12}$, $1$ instead of $[1]_{12}$, etc. (values of
$\Z\_{12}$), **with the express understanding that these values, as well as the value resulting from
any operation on these values, is equivalent to some canonical representation**. We may also
*mangle* notation by using the equality operator $=$ in place of the equivalence operator $\equiv$.

<table>
<colgroup>
<col span='2'><col class='left-border'>
</colgroup>
<thead>
<tr>
<th>Pitch class</th>
<th>Congruence class/value </th>
<th>Pitch class</th>
<th>Congruence class/value </th>
</tr>
</thead>
<tbody>
<tr>
<td>$\text C$</td>
<td>$[0]_{12} \Rightarrow 0$</td>
<td>$\text F\sharp/\text G\flat$</td>
<td>$[6]_{12} \Rightarrow 6$</td>
</tr>
<tr>
<td>$\text C\sharp/\text D\flat$</td>
<td>$[1]_{12} \Rightarrow 1$</td>
<td>$\text G$</td>
<td>$[7]_{12} \Rightarrow 7$</td>
</tr>
<tr>
<td>$\text D$</td>
<td>$[2]_{12} \Rightarrow 2$</td>
<td>$\text G\sharp/\text A\flat$</td>
<td>$[8]_{12} \Rightarrow 8$</td>
</tr>
<tr>
<td>$\text D\sharp/\text E\flat$</td>
<td>$[3]_{12} \Rightarrow 3$</td>
<td>$\text A$</td>
<td>$[9]_{12} \Rightarrow 9$</td>
</tr>
<tr>
<td>$\text E$</td>
<td>$[4]_{12} \Rightarrow 4$</td>
<td>$\text A\sharp/\text B\flat$</td>
<td>$[10]_{12} \Rightarrow 10$</td>
</tr>
<tr>
<td>$\text F$</td>
<td>$[5]_{12} \Rightarrow 5$</td>
<td>$\text B$</td>
<td>$[11]_{12} \Rightarrow 11$</td>
</tr>
</tbody>
</table>

Here are a few examples of values, either on their own or resulting from an operation,
and their corresponding pitch classes:

Value                                  | Pitch class
-------------------------------------- | -------------------------
$1=1$                                  | $\text C\sharp$
$12=0$ (since $12\equiv 0\bmod 12$)    | $\text C$
$13=1$ (since $13\equiv 1\bmod 12$)    | $\text C\sharp$
$1+1=2$                                | $\text D$
$1+10=11$                              | $\text B$
$1+11=0$ (since $12\equiv 0 \bmod 12$) | $\text C$
$3-8=7$ (since $-5\equiv 7 \bmod 12$)  | $\text G$

{% thm %}
In math parlance we can formalize this transformation of the pitch classes into integers
by defining a *map*.

{% thm d Map %}
A map $f:A\mapsto B$ is a function $f$ such that for every $a\in A$ there is a unique $f(a)\in B$,
and the sets $B$ and $A$ are called the image and preimage (or range and domain) respectively.
The names map and function are largely used interchangeably.
{% endthm %}

Fix $P$ the set of musical pitch classes.
Let $g:P\mapsto\Z$ be the map from the pitch classes to congruence classes over the
integers modulus 12, which we define:

$$
\begin{gathered}
g(\text{C}) = [0]_{12} \\
g(\text{C}\sharp/\text{D}\flat) = [1]_{12} \\
\vdots \\
g(\text{A}\sharp/\text{B}\flat) = [10]_{12} \\
g(\text{B}) = [11]_{12}
\end{gathered}
$$

It is worth pointing out that this map is *bijective*.

{% thm d Injective, surjective, bijective %}
A map $f:A\mapsto B$ is called injective, or "one-to-one", if whenever $f(a)=f(b)$ also $a=b$.
In other words, every element in the preimage is mapped to a unique value in the image.

A map $f:A\mapsto B$ is called surjective, or "onto", if for every $b\in B$ there is an element
$a\in A$ such that $f(a)=b$.
In other words, every element in the image is mapped to by $f$, from at least one element in the
preimage.

A map is called bijective if it is both injective and surjective
(a bijective map is also called a bijection).
A function $f$ admits an inverse function $f^{-1}$ if and only if it is bijective.
{% endthm %}

Since $g$ is a bijection, we can map freely between the pitch classes and the congruence classes.
In fact this map is an *isomorphism* between the two sets, but I'll leave it at that and skip
the necessary definitions and explanations for some other time.
{% endthm %}

Pitch classes will allow us to study music in a mathematical way, where we will quantify distances
between notes (intervals), and look at relations between set of notes in terms of operations, i.e.
transposition and inversion.

---

<div class='vf helper' data='random-3-2'></div>

## Intervals

Intervals are nothing new to anyone learned in music theory. However, instead of identifying them by
names like "major third", "perfect fourth", "minor sixth", we'll identify them by the value of the
semitone distance between pitches.

Interval name | Value
-- | --
Unison | 0
Minor second/augmented unison | 1
Major second | 2
Minor third | 3
Major third | 4
Perfect fourth | 5
Augmented fourth/diminished fifth | 6
Perfect fifth | 7
Minor sixth | 8
Major sixth | 9
Minor seventh | 10
Major seventh | 11
Octave | 12

## Normal and prime forms

{% thm d Normal form %}
{% endthm %}

{% thm d Prime form %}
OCPI's ordered least to greatest
{% endthm %}

<!--Unordered pitch interval is the absolute value of ordered pitch interval.-->

Apply $T_{10}$ to the pitch set $[3~4~7]$.

$$
\begin{array}{c} 3 \\ 4 \\ 7 \end{array}
\xrightarrow{T_{10}}
\begin{array}{r}
    3+10 = 13 \equiv 1 \\
    4+10 = 14 \equiv 2 \\
    7+10 = 17 \equiv 5
\end{array}
$$

Apply $I_6$ to the pitch set $[10~11~2]$.

$$
\begin{array}{c} 10 \\ 11 \\ 2 \end{array}
\xrightarrow{I_6}
\begin{array}{r}
    6-10 = -5 \equiv 8 \\
    6-11 = -5 \equiv 7 \\
    6-2  = 4
\end{array}
$$

## Normal form and prime forms

<!--
   -\((0~2~4~5~7)\)
   -
   -But the PCI's of this list are 2, 2, 1, 2.
   -Reversing this list is preferable, as the smallest intervals are at the left: 2, 1, 2, 2.
   -
   -\((0~2~3~5~7)\)
   -->

<!--
   -# Physics of sound
   -
   -## Pitch
   -
   -Where frequency is a measure of vibrations per second, pitch is the
   -corresponding perceptual experience. A single pitch is really just a named
   -frequency, such as middle C being the name for the frequency of 523.251 Hz,
   -a value that doesn't so much roll off of the tongue.
   -
   -## Intervals
   -
   -Individual pitches represent distinct frequencies of sound, and the distances
   -between these distinct pitches are known as *intervals*.
   -
   -### Unisons and octaves
   -
   -When the interval between two frequencies is equal to zero we call it a unison,
   -because for the distance between them to be zero they must be equal. Pitches
   -that are a unison apart have a one to one (1:1) ratio and are identical. When
   -two frequencies have the ratio of two to one (2:1) the interval between them is
   -called an octave, and are considered the same pitch. Pitches that are an octave
   -apart are equivalent to one another but not identical, because although they can
   -be distinguished by sound, they serve the same musical purpose.
   -
   -Pitches can sound the same but be higher or lower in frequency. We call these
   -different octaves of the same pitch. Any octave of a reference pitch can be
   -calculated given the following equation:
   -
   -$$
   -f_x = f_R \cdot 2^x, \quad x \in \mathbb{Z}
   -$$
   -
   -Where $f_R$ is the frequency of the reference pitch, $x$ is the number
   -of octaves above or below the reference pitch (and is an element of the set of
   -all integers [$\mathbb{Z}$)][integers], and $f_x$ is the frequency of
   -the pitch that is $x$ octaves above or below the reference pitch. Examples
   -of integers are 0, 2, 4, and -1.
   -
   -[integers]: https://en.wikipedia.org/wiki/Integer
   -
   -Frequencies of different octaves of A starting with
   -reference frequency $f_R = 440$ (also known as A4 and concert A):
   -
   -$$
   -\begin{array}{ll}
   -x = 0, & \quad f_x = 440 \cdot 2^{0} = 440 \mathrm{~Hz} \\
   -x = 1, & \quad f_x = 440 \cdot 2^{1} = 880 \mathrm{~Hz} \\
   -x = -1, & \quad f_x = 440 \cdot 2^{-1} = 220 \mathrm{~Hz} \\
   -\end{array}
   -$$
   -
   -## Arbitrary intervals
   -
   -Any distance between two pitches make an interval, even if those pitches are the
   -same (unison) or an octave apart. But for these other intervals, we need to
   -extend this formula to [$\mathbb{R}$][real], the set real numbers: of
   -numbers in beyond just integers, and thus intervals between and beyond unisons
   -and octaves:
   -
   -[real]: https://en.wikipedia.org/wiki/Real_number
   -
   -$$
   -f_x = f_R \cdot 2^x, \quad x \in \mathbb{R}
   -$$
   -
   -Where the variable $x$ is now an element of the set of all real numbers
   -$\mathbb{R}$, not just integers.
   -->

---

# Resources

## Setting math and music on the web

Mathematical expressions are displayed using the Javascript library
[KaTeX](https://katex.org/), which is faster than [MathJax][mathjax] and
supports practically all of the same features.
For example, the following code:


```latex
|r|<1 \Rightarrow \sum_{k=0}^\infty ar^k = \frac{a}{1-r}
```

Renders as:

$$
|r|<1 \Rightarrow \sum_{k=0}^\infty ar^k = \frac{a}{1-r}
$$

Musical expressions are displayed using another JavaScript library,
[VexFlow][vexflow], though learning and using it was a pretty involved process.

<!-- Links -->
[mathjax]: https://www.mathjax.org/
[latex]: https://www.mathjax.org/
[VexFlow]: https://github.com/0xfe/vexflow
[lydown]: http://ciconia.github.io/lydown/
[jekyll-katex]: https://github.com/linjer/jekyll-katex

<script type='text/javascript' src='end.js'></script>
