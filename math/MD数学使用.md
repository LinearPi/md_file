###MD数学使用

1. To see how any formula was written in any question or answer, including this one, right-click on the expression it and choose "Show Math As > TeX Commands". (When you do this, the '$' will not display. Make sure you add these. See the next point.)

2. **For inline formulas, enclose the formula in $...$. For displayed formulas, use$$...$$.**
   These render differently. For example, type
   `$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$`
   to show ∑ni=0i2=(n2+n)(2n+1)6∑i=0ni2=(n2+n)(2n+1)6 (which is inline mode) or type
   `$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$`
   to show

   ∑i=0ni2=(n2+n)(2n+1)6∑i=0ni2=(n2+n)(2n+1)6

   (which is display mode).

   ​

3. For **Greek letters**, use `\alpha`, `\beta`, …, `\omega`: α,β,…ωα,β,…ω. For uppercase, use `\Gamma`, `\Delta`, …, `\Omega`: Γ,Δ,…,ΩΓ,Δ,…,Ω.

4. For **superscripts and subscripts**, use `^` and `_`. For example, `x_i^2`: x2ixi2, `\log_2 x`: log2xlog2⁡x.

5. **Groups**. Superscripts, subscripts, and other operations apply only to the next “group”. A “group” is either a single symbol, or any formula surrounded by curly braces `{`…`}`. If you do `10^10`, you will get a surprise: 10101010. But `10^{10}` gives what you probably wanted: 10101010. Use curly braces to delimit a formula to which a superscript or subscript applies: `x^5^6` is an error; `{x^y}^z` is xyzxyz, and `x^{y^z}` is xyzxyz. Observe the difference between `x_i^2` x2ixi2and `x_{i^2}` xi2xi2.

6. **Parentheses** Ordinary symbols `()[]` make parentheses and brackets (2+3)[4+4](2+3)[4+4]. Use `\{` and `\}` for curly braces {}{}.

   These do *not* scale with the formula in between, so if you write `(\frac{\sqrt x}{y^3})` the parentheses will be too small: (x√y3)(xy3). Using `\left(`…`\right)` will make the sizes adjust automatically to the formula they enclose: `\left(\frac{\sqrt x}{y^3}\right)` is (x√y3)(xy3).

   `\left` and`\right` apply to all the following sorts of parentheses: `(` and `)` (x)(x), `[` and `]` [x][x], `\{` and `\}` {x}{x}, `|` |x||x|, `\vert` |x||x|, `\Vert` ∥x∥‖x‖, `\langle` and `\rangle` ⟨x⟩⟨x⟩,`\lceil` and `\rceil` ⌈x⌉⌈x⌉, and `\lfloor` and `\rfloor` ⌊x⌋⌊x⌋. `\middle` can be used to add additional dividers. There are also invisible parentheses, denoted by `.`: `\left.\frac12\right\rbrace` is 12}12}.

   If manual size adjustments are required: `\Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr)` gives (((((x)))))(((((x))))).

7. **Sums and integrals** `\sum` and `\int`; the subscript is the lower limit and the superscript is the upper limit, so for example `\sum_1^n` ∑n1∑1n. Don't forget `{`…`}` if the limits are more than a single symbol. For example, `\sum_{i=0}^\infty i^2` is ∑∞i=0i2∑i=0∞i2. Similarly, `\prod` ∏∏, `\int` ∫∫, `\bigcup` ⋃⋃, `\bigcap` ⋂⋂, `\iint` ∬∬, `\iiint` ∭∭.

8. **Fractions** There are two ways to make these. `\frac ab` applies to the next two groups, and produces abab; for more complicated numerators and denominators use `{`…`}`: `\frac{a+1}{b+1}` is a+1b+1a+1b+1. If the numerator and denominator are complicated, you may prefer `\over`, which splits up the group that it is in: `{a+1\over b+1}` is a+1b+1a+1b+1.

9. **Fonts**

   - Use `\mathbb` or `\Bbb` for "blackboard bold": CHNQRZCHNQRZ.
   - Use `\mathbf` for boldface: ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz.
   - Use `\mathtt` for "typewriter" font: ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz.
   - Use `\mathrm` for roman font: ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz.
   - Use `\mathsf` for sans-serif font: ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz.
   - Use `\mathcal` for "calligraphic" letters: ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZ
   - Use `\mathscr` for script letters: ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZ
   - Use `\mathfrak` for "Fraktur" (old German style) letters: ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz.

10. **Radical signs** Use `sqrt`, which adjusts to the size of its argument: `\sqrt{x^3}` x3−−√x3; `\sqrt[3]{\frac xy}` xy−−√3xy3. For complicated expressions, consider using `{...}^{1/2}`instead.

11. Some **special functions** such as "lim", "sin", "max", "ln", and so on are normally set in roman font instead of italic font. Use `\lim`, `\sin`, etc. to make these: `\sin x` sinxsin⁡x, not `sin x` sinxsinx. Use subscripts to attach a notation to `\lim`: `\lim_{x\to 0}`

    limx→0limx→0

    ​

12. There are a very large number of **special symbols and notations**, too many to list here; see [this shorter listing](http://pic.plover.com/MISC/symbols.pdf), or [this exhaustive listing](https://www.ctan.org/tex-archive/info/symbols/comprehensive/symbols-a4.pdf). Some of the most common include:

    - `\lt \gt \le \ge \neq` <>≤≥≠<>≤≥≠. You can use `\not` to put a slash through almost anything: `\not\lt` ≮≮ but it often looks bad.
    - `\times \div \pm \mp` ×÷±∓×÷±∓. `\cdot` is a centered dot: x⋅yx⋅y
    - `\cup \cap \setminus \subset \subseteq \subsetneq \supset \in \notin \emptyset \varnothing` ∪∩∖⊂⊆⊊⊃∈∉∅∅∪∩∖⊂⊆⊊⊃∈∉∅∅
    - `{n+1 \choose 2k}` or `\binom{n+1}{2k}` (n+12k)(n+12k)
    - `\to \rightarrow \leftarrow \Rightarrow \Leftarrow \mapsto` →→←⇒⇐↦→→←⇒⇐↦
    - `\land \lor \lnot \forall \exists \top \bot \vdash \vDash` ∧∨¬∀∃⊤⊥⊢⊨∧∨¬∀∃⊤⊥⊢⊨
    - `\star \ast \oplus \circ \bullet` ⋆∗⊕∘∙⋆∗⊕∘∙
    - `\approx \sim \simeq \cong \equiv \prec \lhd` ≈∼≃≅≡≺,⊲≈∼≃≅≡≺,⊲.
    - `\infty \aleph_0` ∞ℵ0∞ℵ0 `\nabla \partial` ∇∂∇∂ `\Im \Re` IRℑℜ
    - For modular equivalence, use `\pmod` like this: `a\equiv b\pmod n` a≡b(modn)a≡b(modn).
    - `\ldots` is the dots in a1,a2,…,ana1,a2,…,an `\cdots` is the dots in a1+a2+⋯+ana1+a2+⋯+an
    - Some Greek letters have variant forms: `\epsilon \varepsilon` ϵεϵε, `\phi \varphi` ϕφϕφ, and others. Script lowercase l is `\ell` ℓℓ.

    [Detexify](http://detexify.kirelabs.org/classify.html) lets you draw a symbol on a web page and then lists the TEXTEX symbols that seem to resemble it. These are not guaranteed to work in MathJax but are a good place to start. To check that a command is supported, note that MathJax.org maintains a [list of currently supported LATEXLATEX commands](http://docs.mathjax.org/en/latest/tex.html#supported-latex-commands), and one can also check Dr. Carol JVF Burns's page of [TEXTEXCommands Available in MathJax](http://www.onemathematicalcat.org/MathJaxDocumentation/TeXSyntax.htm).

13. **Spaces** MathJax usually decides for itself how to space formulas, using a complex set of rules. Putting extra literal spaces into formulas will not change the amount of space MathJax puts in: `a␣b` and `a␣␣␣␣b` are both abab. To add more space, use `\,` for a thin space abab; `\;` for a wider space abab. `\quad` and `\qquad` are large spaces: abab, abab.

    To set plain text, use `\text{…}`: {x∈s∣x is extra large}{x∈s∣x is extra large}. You can nest `$…$` inside of `\text{…}`.

14. **Accents and diacritical marks** Use `\hat` for a single symbol x^x^, `\widehat` for a larger formula xyˆxy^. If you make it too wide, it will look silly. Similarly, there are `\bar` x¯x¯ and `\overline` xyz¯¯¯¯¯¯¯¯xyz¯, and `\vec` x⃗ x→ and `\overrightarrow` xy−→xy→ and `\overleftrightarrow` xy←→xy↔. For dots, as in ddxxx˙=x˙2+xx¨ddxxx˙=x˙2+xx¨, use `\dot` and `\ddot`.

15. Special characters used for MathJax interpreting can be escaped using the `\` character: `\$` $$, `\{` {{, `\_` __, etc. If you want `\` itself, you should use `\backslash` ∖∖, because `\\` is for a new line.

(Tutorial ends here.)