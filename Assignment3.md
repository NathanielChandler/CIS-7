
# Nathaniel Chandler  -  CIS 7 - Discrete Structures - Assignment 3
## Part 1:
```
Let S = it is sunny, C = camping is fun, H = the homework is
done, and M = mathematics is easy.
```  
 - [ ] Translate into English: (M → H)∧(S →C)
   - If mathematics is easy, then the homework is done, and if it is sunny, then camping is fun.
 
 - [ ] Translate into Propositional Logic: “Mathematics is easy or camping is fun, as long as it is sunny and the homework is done.”
   - (M v C) ^ (S ^ H)
 
 
## Part 2: 
 - [ ] Use a truth table to determine whether this is a tautology, contradiction, or neither:  (¬B → ¬A) → ((¬B → A) → B)
 
| A | B | ¬A | ¬B | ¬B -> ¬A | ¬B -> A | ((¬B -> A) -> B | (¬B → ¬A) → ((¬B → A) → B)
|---|---|--- |--- | -------- | ------- | --------------- | --------------------------
| T | T | F  | F  | T        | T       | T               | T
| T | F | F  | T  | F        | T       | F               | T
| F | T | T  | F  | T        | T       | T               | T
| F | F | T  | T  | T        | F       | T               | T

   - Tautology
 
  - [ ] Use a truth table to determine whether this is a tautology, contradiction, or neither:  ((A → B)∧(B → ¬A)) → A
 
| A | B | ¬A | A → B    | B -> ¬A | (A → B)∧(B → ¬A) | ((A → B)∧(B → ¬A)) → A
|---|---|--- | -------- | ------- | ---------------- | --------------------------
| T | T | F  | T        | F       | F                | T
| T | F | F  | F        | T       | F                | T
| F | T | T  | T        | T       | T                | F
| F | F | T  | T        | T       | T                | F
 
   - Neither
 
  
## Part 3:
```
For each of the following pairs of propositions, show that the
two propositions are logically equivalent by finding a chain of equivalences from one
to the other. State which definition or law of logic justifies each equivalence in the
chain.
```
 - [ ] (p ∧ q) → r <=> p → (q → r )
   - (p ∧ q) → r <=> p → (q' v r )               :    Implication
   - (p ∧ q) → r <=> p' v (q' v r )              :    Implication
   - (p ∧ q) → r <=> (p' v q') v r               :    Associative
   - (p ∧ q) → r <=> (p ^ q)' v r                :    DeMorgan's Law
   - (p ∧ q) → r <=> (p ∧ q) → r                 :    Implication
 
 - [ ] (q ∨ r) → p <=> (q → p)∧(r → p)
   - (q ∨ r) → p <=> (q' v p)∧(r' v p)             :    Implication
   - (q ∨ r) → p <=> (p v q')∧(p v r')             :    Communiative
   - (q ∨ r) → p <=> p v (q' ^ r')                 :    Distributive
   - (q ∨ r) → p <=> (q' ^ r') v p                 :    Communiative
   - (q ∨ r) → p <=> (q v r)' v p                  :    DeMorgan's Law
   - (q ∨ r) → p <=> (q v r) → p                   :    Implication
 
## Part 4:
```
Let Loves(x,y) mean “x loves y,” Traveler(x) mean “x is a traveler,”
City(x) mean “x is a city,” Lives(x,y) mean “x lives in y.”
```
 - [ ] Translate into English: ∃x∀y∀z(City(x)∧Traveler(y)∧Lives(z,x)) → (Loves(y,x)∧ ¬Loves(z,x))
   - If there exists a City and every Traveler exists and every Citizen lives in that city, 
   then every Traveler loves that city, and every Citizen does not love that city.  
 
 - [ ] Translate into Predicate Logic: “No traveler loves the city they live in.”
   - ∀y[Traveler(y) -> ∃x((City(x)^Lives(y,x)) -> ¬Loves(y,x))]
 
  
## Extra Credit:
```
Assuming: p → (q ∧ r ), s → r , r → p
Prove: s → q.
```
- r → q <=> p → (q ∧ r )            : Modus Ponen
- p → q <=> p → (q ∧ r )            : Modus Ponen
- p → q <=> (p → q) ∧ (p → r)       : Distributive
- p → q <=> (p → q) ∧ (p → p)       : Modus Ponen
- p → q <=> (p → q) ∧ T             : Tautology
- p → q <=> p → q                   : Identity


```
Assuming: ¬(r ∨ s), ¬p → s, p → q. 
Prove: q
```
  
