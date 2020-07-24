## Introduction
{:#introduction}

One fundamental part of the [Linked Data principles](cite:cites LinkedDataPrinciples) is the usage of open Web specifications.
This concept is important because Linked Data should not require specific tools or services,
but it should be software-independent.
This means that anyone should be able to implement these specifications,
and that the resulting software should be able to handle Linked Data
that may have been produced by other implementations.

When implementing a specification, it is crucial that the resulting implementation is _correct_ according to a specification.
Concretely, this means that all specified cases must produce the correct result.
For example, a parser implementation for the [JSON-LD 1.1 syntax specification](cite:cites jsonld)
must produce the expected RDF triples for given JSON-LD documents.

Most Linked Data-related specifications make use of declarative test suites.
These test suites are represented in RDF, and are published via the Linked Data principles.
Historically, the [RDF Data Access Working Group (DAWG)](http://www.w3.org/2001/sw/DataAccess/)
was the first to define such a test suite for the [SPARQL query language](cite:cites spec:sparqllang).
The DAWG defined the test manifest vocabulary that allows one or more _tests_ to be included in a _test manifest_.
Each test defines a certain _action_ and a corresponding _result_.
In the case of the SPARQL test suite,
this action describes a SPARQL query with a dataset,
and the result describes a SPARQL query result.
In order for implementations to prove their compliance to the SPARQL specification,
they need to execute all tests in this test suite.
The test results for such test suites are typically represented using the [EARL vocabulary](cite:cites earl),
which allows test assertions to be represented about whether or not given software passes a certain test.
Since this test manifest vocabulary from the DAWG has proven to be a robust basis for representing test manifests,
it has been adopted by many other specifications to represent their test suite,
such as [JSON-LD](cite:cites jsonld), [Turtle](cite:cites turtle), and [RDFa](cite:cites rdfa).
Each of these test suites are being maintained by the [RDF Tests W3C Community Group](https://github.com/w3c/rdf-tests){:.mandatory}.
An example of such a test suite can be seen in [](#example-manifest).

<figure id="example-manifest" class="listing">
````/code/manifest.txt````
<figcaption markdown="block">
Part of the [manifest](https://w3c.github.io/json-ld-api/tests/toRdf-manifest.jsonld) of the JSON-LD 1.1 parsing test suite.
</figcaption>
</figure>

While the availability of declarative test suites is highly beneficial for ensuring specification compliance,
the fact that they are not directly executable can lead to a large overhead for developers.
A developer wanting to execute a test suite against an implementing has to go through the following steps:

1. **Download** the test manifest
2. **Parse** the manifest based on a certain RDF syntax
3. **Follow links** to other parts of the manifest if applicable
4. **Interpret** the test definitions as executable logic
5. **Execute** all tests
6. **Report** the test results

Unfortunately, these steps require a significant implementation effort,
which adds an additional burden next to the developer's implementation effort of the specification.
In order to alleviate this burden, we introduce a JavaScript tool called _RDF Test Suite_
that abstracts these steps in a developer-friendly way.
This tool allows developers to focus on the part they are really interested in,
i.e., implementing a specification.
While testing specification compliance is important,
it should not require more effort from the developer than calling a single command,
which is exactly what RDF Test Suite provides.

In this article, we report on the implementation of RDF Test Suite,
how it can be used,
and what the future steps are.
