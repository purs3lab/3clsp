---
layout: default
title: Home
nav_order: 1
description: "This tool helps you convert your unsafe legacy C code to a more memory safe C code"
permalink: /
---

# A better &  easier way to convert your unsafe C code
{: .fs-9 }

3CLSP gives you the power to convert your **legacy C code** to a memory-safe version of C called **CheckedC**. 
{: .fs-6 .fw-300 }

## Introduction
CheckedC was developed by Microsoft as an extension to the regular **C** we know and love but adds checking to C to detect or prevent common programming errors such as buffer overruns, out-of-bounds memory accesses, and incorrect type casts. We leverage the use of **3C** which works on legacy C code and annotates pointers and infers bounds for those pointers based on their callers and context. We created an extension to the _clangd_ LSP framework that understands your C/C++ code and adds smart features to your editor like code completion, compile errors, go-to-definition and more.