## Implementation
{:#implementation}

A first design goal of our tool is that it should _easily fit_ into the developer's tool chain,
and should behave in a manner that is familiar to developers.
As such, we designed RDF Test Suite to behave similar to JavaScript testing frameworks
such as [Jest](https://jestjs.io/){:.mandatory} and [Mocha](https://mochajs.org/){:.mandatory}.
A second design goal is that the tool should be _generic_ enough so that it can be used for different types of test suites,
instead of being hardcoded to support only one very specific test suite.
For this, we opted for a _modular_ architecture in which support for spec-specific features can be added without having to change any core logic.

We have implemented RDF Test Suite in TypeScript, which is a typed superset of JavaScript.
It is available under the MIT license on [GitHub](https://github.com/rubensworks/rdf-test-suite.js){:.mandatory}.
Furthermore, it is available for download on the [npm packager](https://www.npmjs.com/package/rdf-test-suite){:.mandatory}.
At the time of writing, it is confirmed to handle the test suites of SPARQL 1.1 Query, RDF/XML, N-Triples, N-Quads, Turtle, Trig, JSON-LD, RDFa, and N3.
