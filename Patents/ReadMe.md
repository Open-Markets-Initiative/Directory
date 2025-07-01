# The Three Generations of Source Generators and related IP

## First Generation: Inefficient, One-to-One Tools

The earliest efforts in binary protocol source generation emerged in the 1990s. These systems followed a **one-to-one or one-to-few** model, in which a tool could emit code for a limited number of languages based on a structured symbol table or domain-specific language.

* **Example:** [US7401326B1 (2002)](https://patents.google.com/patent/US7401326B1/en)
  This patent outlines a generator using a protocol database to output code in several languages, but the complexity and size of the generator itself often rivaled the code it produced. These systems were brittle and tightly coupled to specific formats or languages.

## Second Generation: XML-Based Message Models

By the mid-2000s and 2010s, the field matured into **more capable but still narrowly scoped tools**. These generators adopted XML-based or other interface description languages (IDLs) and offered partial support for financial binary formats like market data feeds.

* **Example:** [US8321465B2 (2005)](https://patents.google.com/patent/US8321465B2/en)
  This system could handle binary messages with repeating groups, optional fields, and some custom field support. However, it was **message-centric**, lacking support for arbitrary headers or general binary data constructs. Tools like [Simple Binary Encoding (SBE)](https://github.com/real-logic/simple-binary-encoding) mirrored this design and gained traction in financial low-latency systems, but remained limited by their rigid format and assumptions.

* **Kaitai Struct (2015)** provided a major usability improvement with its declarative DSL for arbitrary binary formats, but it still followed a **one-to-many** model using a fixed IDL and couldn't support complex or evolving protocol requirements at scale.

## Third Generation: The OMI Breakthrough

The Open Markets Initiative introduced a **third generation** of source generators designed to overcome the limitations of its predecessors. This system employs a **many-to-many architecture**, decoupling input formats from output targets via **generic intermediate representations**.

* **US12101388B2 (2022)** – [Universal Binary Specification](https://patents.google.com/patent/US12101388B2/en)
  Enables normalization of any binary interface description or informal documentation.

* **US20240419416A1 (2024)** – [Binary Data Model Compiler](https://patents.google.com/patent/US20240419416A1/en)
  Introduces a multistage pipeline that separates parsing, normalization, transformation, and emission. This allows OMI’s system to **ingest nearly any binary protocol format** and **emit optimized, production-ready code across languages** — something no previous generation could claim.

OMI’s patented architecture provides:

* True protocol abstraction
* Full support for arbitrary binary structures, not just messages
* Extensibility through a generic, versioned intermediate form
* Scalable generation for dozens of languages and runtime environments

## Why It Matters

Previous generations were constrained by their tight coupling to single IDLs, language-specific quirks, or assumptions about message structure. OMI’s third-generation approach unlocks full automation for even the most opaque or proprietary binary data feeds — including those used in high-frequency trading and other latency-sensitive applications.
