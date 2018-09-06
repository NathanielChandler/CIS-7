
 Show that p->q and q' -> p' are logically equivalent without using truth tables or a "contrapositive" law (don't assume they are true)
 ---
    p->q <=> q' -> p'
    'p v q <=> ('q)' v p'     Implication
    'p v q <=> q v p'         Double Negation
    'p v q <=> 'p v q         Communinative
 
 Show that (p->r) ^ (q->r) <=> (p v q) -> r
 ---
    (p->r) ^ (q->r) <=> (p v q) -> r
    ('p v r) ^ ('q v r) <=> (p v q) -> r   Implication
    (r v 'p) ^ (r v 'q) <=> (p v q) -> r   Communiative
    r v ('p ^ 'q) <=> (p v q) -> r         Distributive
    ('p ^ 'q) v r <=> (p v q) -> r         Communiative
    (p v q)' v r <=> (p v q) -> r          DeMorgan's Law
    (p v q) -> r <=> (p v q) -> r          Implication
 
 Give an interpretation to prove that the following wff is not valid: (Ǝx)A(x) ^ (Ǝx)B(x) -> (Ǝx)(A(x) ^ B(x))
 ---
      if x = programmers, A(x) = programmers who use the light theme, B(x) = programmers who use the dark theme
      Some programmers use the light theme, and some programmers use the dark theme.
      There are no programmers that use the light theme and the dark theme.
 
