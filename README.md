# cleanCode
Lessons from Uncle Bob

# 1. Clean Code
## The Total Cost of Owning a Mess
Teams that move fast at the beginning slow to a crawl as time passes.
If every modification requires tangles/twists/knots to be understood
so that more tangles/twists/knots can be added, over time the mess becomes
impossible to clean up.

## We Are Authors
We are _responsible_ for communicating well with our readers.

Ratio of time spent reading vs. writing code is well over 10:1.

_Making it easy to read actually makes it easier to write code._

## The Boy Scout Rule
_Leave the campground cleaner than you found it._

Can you imagine working on a project where code _simply got better_ as 
time passed?

We should all check-in our code a little cleaner than when we checked it out.
Cleanup doesn't always have to be something big. It could be changing one variable
name for the better, breaking up one function that's too large, eliminating
duplication, cleaning up composite if statements.

# 2. Meaningful Names
## Intention-Revealing Names
```
elapsedTimeInDays;
daysSinceCreation;
daysSinceModification;
fileAgeInDays;
```
Names should provide _context_ to _model_ the program being described.

## Avoid Disinformation
```
XYZControllerForEfficientHandlingOfStrings
XYZControllerForEfficientStorageOfStrings
```
Don't obscure the meaning with false clues.

## Make Meaningful Distinctions
```
copyChars(a1, a2)
copyChars(source, destination)
```
Noninformative names provide no clue to the author's _intention_.
```
Product
ProductInfo
ProductData
```
Noise words don't make it mean anything different and are redundant.

## Use Pronounceable Names
Don't use acronyms, programming is a social activity and you can't
discuss code if you can't read it out loud.

## Use Searchable Names
```
e
i,j,k
4
```
Imagine having to grep 'e' or search for magic constants

## Avoid Encodings
```
IShapeFactory
PhoneNumber phoneString;
```
Don't add types/scopes into names.

## Avoid Mental Mapping
Don't force readers to map ```a``` to ```account```

## Class Names
Class names should be NOUNS or NOUN PHRASES. Avoid ambiguous words
like Manager, Processor, Data, Info. A class name should NEVER be
a VERB.

## Method Names
Method should be VERBS or VERB PHRASES.
```
postPayment
deletePage
save
paycheck.isPosted
```
Use get, set, is/has for accessors, mutators and predicates.

```
Complex.fromRealNumber(23.0)
new Complex(23.0)
```
Use static factory methods with names that describe arguments

## Don't Be Cute
```
whack()
```
whack() isn't exactly kill(). Neither is holyHandGrenade().

## Pick One Word Per Concept
!important
```
fetch
get
retrieve

add
insert

controller
manager
driver
```
Pick one word for one abstract concept and keep this lexicon consistent.
Probably document it somewhere

## Don't Pun
```
add
insert
append
```
Avoid using the same name for two purposes.

## Use Problem Domain Names
```
velocity
speed

deltaX
xDisplacement

blackjack
scoreIs21
```
Problem domain usually has more concise, meaningful descriptions about the problem
than programmers.

## Add Meaningful Context
```
firstName
lastName
street
houseNumber
city
state
```
What if you just saw ```state``` on its own? Would it be obvious what 'state' means?

Put them in a class called ```Address``` and the context becomes clear.

## Don't Add Gratuitous Context
See section above on Avoid Disinformation. If 10 of 17 characters of your name are
redundant or irrelevant, you should probably use a shorter name.

```
accountAddress
customerAddress
```
Make sense if they are _instances_ of Address, but are poor _class_ names.

```
PostalAddress
MAC
URI
```
Precisely naming addresses to avoid ambiguity between MAC addresses, Web addresses
and port addresses.

