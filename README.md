# Expandable Expressions
Here, I am defining a new type of expression. These expressions (&ldquo;Expandable Expressions&rdquo;, or ExExps) are concerned with the compression of information. An ExExp will be expressed like this in this document: `/[body]/[flags]`. The implemenation, however, can be in any form.

## Statements, etc.

 * A _switch_ statement: _b_<sub>0</sub>(_a_<sub>1</sub>~_a_<sub>2</sub>~&hellip;~_a_<sub>N</sub>)_b_<sub>1</sub>. This returns a string that contains all possible combinations of either _a_<sub>1</sub>, _a_<sub>2</sub>, &hellip; or _a_<sub>N</sub> surrounded by _b_<sub>0</sub> and _b_<sub>1</sub>, with _a_<sub>k</sub> being a string of characters. A shortened switch statement looks like this: _b_<sub>0</sub>~(_a_<sub>0</sub>_a_<sub>1</sub>&hellip;_a_<sub>N</sub>), where _a_<sub>k</sub> is a single character.
  * `/H(ello~i)/ => [Hello, Hi]`
  * `/(C~B~H)at/ => [Cat, Bat, Hat]`
  * `/~(CBH)at/ => [Cat, Bat, Hat]`
  * `/~(BC)a~(rt)/ => [Bat, Cat, Bar, Car]`
  * `/~(AB)~(DEF)(GH~IJ~KL)/ => [ADGH, ADIJ, ADKL, AEGH, AEIJ, AEKL, AFGH, AFIJ, AFKL, CDGH, CDIJ, CDKL, CEGH, CEIJ, CEKL, CFGH, CFIJ, CFKL]`


## Flags
 * `c`ompress - Puts `switch`ed statements within sub-arrays. So, `/~(BC)a~(rt)/c => [[Bat, Cat], [Bar, Car]]` and `/~(AB)~(DEF)(GH~IJ~KL)/c => [[[ADGH, ADIJ, ADKL], [AEGH, AEIJ, AEKL], [AFGH, AFIJ, AFKL]], [[CDGH, CDIJ, CDKL], [CEGH, CEIJ, CEKL], [CFGH, CFIJ, CFKL]]]`
