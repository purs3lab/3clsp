---
layout: default
title: FAQs
nav_order: 6
---
# [](#header-1) Caution

The tool does it's best to try to convert as much code as possible but sometimes in cases where the code might need major refactoring. If you have some parts of the code that are wrapped in an `_Unchecked` block, the best steps would be go over the *CheckedC* document and familiarising yourself with the language. 

Most of the time, the cause of unchecked blocks is *Incorrect bounds inferrence* or *variable argument functions*.

So we do not make the claim that running your code through this tool would give you a perfectly converted safe code. We tool will make sure to convert as much as possible so you can focus on the parts of code that are still unsafe and needs developer intervention.

Compiling the converted code is a good way to find out the unsafe segments in the code, because these segments would generally cause the compilation to fail.