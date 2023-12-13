# General Syntax Tutorials

You may want to get straight into patch manager patching, which is fine, in that case you can skip ahead to the
[Part Patching Tutorials](Part-Patching-Tutorials.md), but it is highly recommended that you understand at least the
basics of how the language works beforehand.

## Basic Syntax Tutorials
These tutorials are here to help you understand the absolute basics of Patch Manager patching
- [Rulesets, Selectors, and Selection Blocks](Rulesets-Selectors-and-Selection-Blocks.md) explains the most fundamental
construct that Patch Manager has.
- [Selection Actions](Selection-Actions.md) explains what actions can be taken within that most fundamental construct.
- [Values, Variables, and Expressions](Values-Variables-and-Expressions.md) explains ways to express and manipulate data
within Patch Manager.
## Intermediate Syntax Tutorials
These tutorials describe some intermediate concepts within the syntax, in no necessary order.
- [Top Level Statements](Top-Level-Statements.md) explains all the top level statements that can be done with Patch Manager
rather than just the Selection Block
- [Libraries](Libraries.md) explains a way to encapsulate parts of your patches such that they can be reusable, and also
such that other mods can use them.
- [Selection Block Attributes](Selection-Block-Attributes.md) explains a part of selection blocks that was not touched on
in the page for them in the basic section, but can be useful for both ordering, and toggling selection blocks.
## Advanced Syntax Tutorials
These tutorials provide explanations of the more advanced syntax constructs within patch manager, again in no necessary order.
- [Mixins](Mixins.md) explains a useful way to template common patches with arguments.
- [Functions and Closures](Functions.md) explains how to create reusable sequences of expressions, how to use them, and
how to use the builtin ones as well
- [Class Capture Selector](Class-Capture-Selector.md) explains the most advanced of the selectors that was left out of
the page on selectors in the basic section, but arguably one of the most powerful ones.