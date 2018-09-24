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

## Use Solution Domain Names
Use CS terms, algorithm names, design pattern names, etc. 
People who read your code will be programmers.

Don't draw every name from the _problem_ domain if there is a known
_solution_ domain for it.

```JobQueue``` should be obvious to people who understand data
structures, and ```GameState``` would make sense to someone who
knows the State design pattern.

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

#  3. Functions

## Small!
The first rule of functions is that they should be small.

The second rule of functions is that _they should be smaller than that._

## Do One Thing
Functions should do one thing They should do it well. They should do it only.

Blocks within if, else, while statements should be one line long, probably
a function call.

Functions should also not be large enough to hold nested structures.

Functions that do one thing cannot be reasonably divided into sections. If you have
to comment out sections, this is an obvious symptom.

## Levels of abstraction below function name
```java
public static String renderPageWithSetupsAndTeardowns(
    PageData pageData, boolean isSuite) throws Exception {
        if (isTestPage(pageData)) {
            includeSetupAndTeardownPages(pageData, isSuite);
        }
        return pageData.getHtml();
    }
```
We can describe the function as a brief _TO_ paragraph:

TO RenderPageWithSetupsAndTeardowns, we check to see whether the page is a test page
and if so, we include the setups and teardowns. In either case we render the page in HTML.

If the function does only those steps that are _one level_ below the stated name of the function,
then the function is doing _one_ thing. It would be hard to meaningfully shrink this code example - 
we can extract the ```if``` statement into a function includeSetupAndTeardownPages_IfTestPage_ but
that simply _restates_ the code _without changing the level of abstraction._

TLDR: A function is doing more than one thing _if you can extract another function from it with a
name that is not merely a restatement of its implementation._

## One Level of Abstraction per Function
Mixing levels of abstraction is always confusing.

Readers cannot tell if an expression is an essential concept or a detail.

Worse, the broken windows theory states that once details are mixed in with essential concepts, 
more and more details fester within the function...

## _The Stepdown Rule_
We want to read the program as though it were a set of _TO_ paragraphs:

> TO include the setups and teardowns, we include setups, then we include the test page content
> and then we include the teardowns.
>   TO include the setups, we include the suite setup if this is a suite, then we include the 
>   regular setup.
>   TO include the suite setup, we search the parent hierarchy for the 'SuiteSetUp' page and
>   add an include statement with the path of that page.
>   TO search the parent ...

Practise writing functions that stay at a single level of abstraction.


# 6. Objects and Data Structures

## Data Abstraction
A class does not simply push its variables out through getters and setters. Rather it exposes
abstract interfaces that allow its users to manipulate the _essence_ of the data, without
having to know its implementation.

## Data/Object Anti-Symmetry
**Objects hide their data behind abstractions and expose functions that operate on that data.
Data structures expose their data and have no meaningful functions.

Go back and read that again.**

The complimentary nature/virtual opposites of procedural code and OOP is a fundamental dichotomy:

_Procedural code (code using data structures) makes it easy to add new functions without changing
the existing data structures. OO code, on the other hand, makes it easy to add new classes without
changing existing functions.

Procedural code makes it hard to add new data structures because all the functions must change.
OO code makes it hard to add new functions because all the classes must change._


