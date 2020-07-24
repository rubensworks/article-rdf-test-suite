## Conclusions
{:#conclusions}

The RDF Test Suite has been shown to significantly aid developers in achieving and testing specification compliance,
by removing the overhead of test suite interpretation and execution.
It is in use by multiple key RDF libraries for JavaScript.
Not only does it simplify test suite _execution_, it also simplifies test suite _development_
thanks to its advanced feature for [temporarily injecting local files into a test suite](https://github.com/rubensworks/rdf-test-suite.js#map-urls-to-local-files).
This simplified the creation of several tests for the JSON-LD test suite within the JSON-LD 1.1 Working Group.

In future work, we will add support for more test suites, such as SPARQL 1.1 Update and JSON-LD 1.1 framing.
Furthermore, we aim to set up a service around this tool in which test suites can be executed against registered libraries,
with the option to publicly display the test results.
Such a service would allow developers to register their library for continuous test suite evaluation,
and library users to easily choose certain tools based on their test results and specification compliance.
