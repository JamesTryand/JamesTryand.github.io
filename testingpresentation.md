name: testing
class: middle 
layout: true

---
# Perfect Testing and Why nulls Mean You Need To Keep Designing.  
---

# We Don't Want To Test  
<!--
.center[![Right-aligned image](https://images-na.ssl-images-amazon.com/images/G/01/img15/pet-products/small-tiles/23695_pets_vertical_store_dogs_small_tile_8._CB312176604_.jpg)]
-->
- Sounds Great but in the real world...  
--

- They keep breaking
--

- Waste of time / effort I just wanna code  
--

- Don't know where to start  
---
# Testing Smells  
* Not Inverting the Pyramid
* Coverage via Constructor Test
* Not refactoring
* Brittle Test
---
# The Purpose of Tests
- Confirmation of Spec
???
ensure model find missing edges in code & design
--

- Exploration of code
--

- Exploration of problem space
--

- Confidence in your codebase
--

- Documentation & Examples
---
# Key Cause of Bugs

- Unexpected Code Paths
--

  - Unreasoned about code
--

  - **why**
--

  - *Cognitive Load is Too High
---
class: middle,center
# Key Cause of Bugs

**because it's...**
## "Big and Complicated"
---

# Can we do something different?  
--

## Don't Make it Big  
--

## Don't Make it Complicated  
--

## Simply Avoid The Problem  
---

# HOW?
---

# Write "Better" Code
--

# Write "Better" Tests
---

# Write "Better" Code => 
* Code that avoids the problems  

# Write "Better" Tests => 
* Tests that prevent and capture possible errors
---

## A short background
"Cognitive Load Is Too High"
---
## So what is cognitive Load?
## Why is it important?
???
Attention and Digit Span
Mental Model Theory
---
**IS IT NOT TRUE THAT? LONDON IS A CITY AND EUROPE IS A COUNTRY**  
---
a) London is not a city and Europe is not a continent.  
b) London is not a city or Europe is not a continent, or both.  
c) If London is not a city, then Europe is not a continent.  
d) London is not a city or else Europe is not a continent.  
---
## Reasoning Blindspots
???
we are better at reasoning about positives rather than negatives
the number of mental steps indicates difficulty
---
## So how do we avoid them.
---
# Reduce the Cognitive Load
## By Making It Less Complex
## But How?
---
# Avoid the 'Excel Form'
* "It will be easy because it does all this for you"
---
# Geometric Complexity
* the number of discrete tests = 
* Multiplying each parameter's possible number of states
ie. 
X{3}, Y{5}, Z{3}
3*5*3 = 45
vs. indpendently testing states becomes
3+5+3 = 11
---
# Some Coding Techniques  
## Favor Value Oriented Programming Over Place Oriented Programming  
---
## Values vs Places 
* Facts are not places that you change
* Facts are Values
* Facts do not change
* So use immutable Values
???
---
# Values
* Do Not Change
* can be composed of other values
* aggregate down to values
* can be shared
---
# Values
* Reproducable Tests
* Easy to Fabricate
* Language Independent
---
# Values
* Form our Interfaces
* Reduce Coordination
* Something that happened
---
# Great. So?
---
# Use immutability
* If it's wrong it was only where it was made.
* Can be shared - Concurrency becomes trivial
--

# But We Need State In Our System
---
# Merging Parameters
* By simplifying down input / output parameters to a single input / output state type...
--

# Wat?
---
# Union Types
(types that are a union of other types)  
ie. string | int | error  
???
* Then where you have that type, you know to handle each possible option.  
* By discriminating between them, there's confidence you're not missing any  
* Cognitive load is reduced because it's transparent what each one is  
---

# Benefits Of Union Types
* explicit description & handling lowers cognitive load
* confidence code paths are not missed.
---
# But I work in the real world...
---
# Enter the NULL
* its an escapes hatch from the typing system
* "My Billion Dollar Mistake"
* So a 'null reference exception' is a missed codepath
???
* Which means a use case you have but did not model for...
* ...so back to the drawing board
---
# BACK TO TEST IMPROVEMENTS
* okay so immutability gives us easier tests 
* prior state change -> THE TEST -> expected events
## But where do i start?
---
# SCIENCE
* cannot prove the positive - only disprove something
--

* so disprove the negative
--

* "But Cognitive Load!"
* ahh yes.
---
# Embrace the Failure
* you should know or expect the code to have certain properties
* figuring out what to do if it goes bad...
* if you disprove that - you have a working system
--

* once that is in place reduce the number of ocassions you defer to your error handler.
* use property based testing will help to do this
* This will avoid exceptions as they are a seperate workflow in your system
---
# Anything else
* KISS - don't overengineer during testing, use minimal and then should the need arise use big
* Don't make assumptions about usage behaviour - let it emerge in the refactor
* FLOW & FEEDBACK
  * copy test;
  * modify test;
  * put fixing code in test to pass test;
  * refactor by putting it in the right place
  * and clean up
  * commit

---
# RECAP
## Use Good Coding Techniques To Help Reasonability
* Immutability 
* Discriminated Unions
* Small Pieces
---
# RECAP
* Test the expected behaviours
* Start by handling failure in tests and code
* Then reduce the errors by confirming the properties don't fail
* Keep Flow Tight:
---
# References

## Immutability  

## Cognitive Science  
* https://www.researchgate.net/publication/281258035_The_shallow_processing_of_logical_negation/download 
* https://ejop.psychopen.eu/article/view/696/html 

## Union Types

## State Modelling 

## Property Based Testing

## Values

## Reducing Complexity


???
https://remarkjs.com/remarkise
