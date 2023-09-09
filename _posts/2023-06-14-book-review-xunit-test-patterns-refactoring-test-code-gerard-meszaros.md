---
title: "Book review: xUnit Test Patterns: Refactoring Test Code (Gerard Meszaros)"
date: 2023-06-14
tag: book review
---

This is a huge, comprehensive book, containing every testing pattern I knew of and many more.

The first ~200 pages build up a convincing narrative of philosophies and practices around automated testing strategy, touching on important patterns as they come up.

The remaining ~600 pages explain each smell and pattern in detail. This pattern catalogue shouldn't be read front to back. I skimmed it, and paid more attention to interesting or important patterns. I'm sure I will refer back to it in the future.

The most interesting set of patterns for me are the ones related to test doubles. The author's categorisation of different types of test double (stubs, spies, mocks and fakes) clears up a lot of the arguments seen online about the subject, and helped me to understand the different reasons we replace dependencies during tests. For example, mocking is useful if you need to verify indirect outputs (if they would otherwise be untested), and stubbing is useful if I need to provide specific indirect inputs (e.g. to inject an exception or another output that's hard to generate from the real dependency).

The strength of this book is that it doesn't present just a single view of testing, but many. The author treats each point of view fairly and respectfully, explaining the rationale behind every pattern, where it can be useful, and what are its drawbacks.

The only thing I think was missing from this book was: what should the system under test be? One class, one module? Should you test non-public classes and methods? Should you test only through the ports of the ports and adapters pattern? It's mentioned that it's best to test through the "front door", i.e. the public API, and that system-level tests can test through the UI or, ideally, directly on the service layer, and in most of the examples it's implied that we're only testing one class or a small group of related classes. It would have been interesting to read some discussion specifically about test granularity.