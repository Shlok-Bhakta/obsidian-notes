# Definition
A compound [[Proposition]] that is always true, no matter the values

# Notes
- Opposite of [[Contradiction]]  

# Example
show that (p ∧ q) -> (p ∨ q) is a [[Tautology]] 

(p ∧ q) -> (p ∨ q) ≡ ¬(p ∧ q) ∨ (p ∨ q) by the conditional disjunction equivalence

¬(p ∧ q) ∨ (p ∨ q) ≡ (¬p ∨ ¬q) ∨ (p ∨ q) by [[De Morgan's Laws]] 

(¬p ∨ ¬q) ∨ (p ∨ q) ≡ ¬p ∨ (¬q ∨ (p ∨ q)) by the associative law

¬p ∨ (¬q ∨ (p ∨ q)) ≡ ¬p ∨ ((¬q ∨ p) ∨ q) by the communitive law

¬p ∨ ((¬q ∨ p) ∨ q) ≡ ¬p ∨(p∨T) ≡ T by the associative and domination law