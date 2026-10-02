### Reflection

**1. What did NumPy hide from you, and why was it still important to learn the loop version first?**

NumPy hid the loop itself. `temps.mean()` runs an optimized C loop I never see.
Learning the loop first in Week 3 taught me *what* a mean actually is — sum ÷ count.
Without that, `.mean()` would just be magic. The loop built the concept; NumPy made
it fast. I trust `.mean()` today because I could once write it by hand.

**2. One insight about Kigali's weather my analysis revealed.**

Kigali's temperatures are very stable — the std is small, and dry days are slightly
warmer on average than rainy days. Rainfall is concentrated: most days are dry, and
a handful of heavy-rain days contribute most of the total. The season's first half
was [warmer/cooler] than the second — see 5.2 output.



