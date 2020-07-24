## Usage
{:#usage}

In order to use RDF Test Suite on the command line, at least two arguments need to be passed:

1. Path to a JavaScript engine file
2. URL of a test manifest

The JavaScript file must point to an implementation of a specific interface, which depends on the test suite.
For example, if syntax parsing tests are being executed, an [`IParser`](https://github.com/rubensworks/rdf-test-suite.js/blob/master/lib/testcase/rdfsyntax/IParser.ts) interface is required,
while [`IQueryEngine`](https://github.com/rubensworks/rdf-test-suite.js/blob/master/lib/testcase/sparql/IQueryEngine.ts) must be passed for query execution tests.
The exact implementation is up to the developer, as only the specified interface is relevant to RDF Test Suite.
Since RDF Test Suite runs on Node.js, other programs can be invoked from JavaScript via the [`child_process` module](https://nodejs.org/api/child_process.html),
which means that non-JavaScript implementations can also be tested with this tool.

By default, _all_ tests from the manifest and its dependencies will be executed against the given implementation.
Optionally, the user can decide to [filter tests](https://github.com/rubensworks/rdf-test-suite.js#test-filtering)
if only one or a few tests need to be executed.
Since large test suites can require many HTTP requests to be executed,
the test suite can optionally be [cached](https://github.com/rubensworks/rdf-test-suite.js#enabling-http-caching).
By default test results will be printed in a compact human-readable format,
but the results can optionally also be [formatted in an EARL report](https://github.com/rubensworks/rdf-test-suite.js#earl-output).
Additional details on more advanced features can be found in the [RDF Test Suite readme](https://github.com/rubensworks/rdf-test-suite.js#readme){:.mandatory}.

So far, RDF Test Suite is actively being used in more than 15 JavaScript libraries,
such as the [Comunica SPARQL query engine](cite:cites comunica),
the [parsers of N3.js](https://github.com/rdfjs/N3.js){:.mandatory},
and a [streaming JSON-LD parser](https://github.com/rubensworks/jsonld-streaming-parser.js){:.mandatory}.
[](#example-exec) shows an example of RDF Test Suite being executed by the streaming JSON-LD parser.

<figure id="example-exec" class="listing">
````/code/exec.txt````
<figcaption markdown="block">
Part of the JSON-LD 1.1 parsing test suite results when executed against the [streaming JSON-LD parser](https://github.com/rubensworks/jsonld-streaming-parser.js).
</figcaption>
</figure>
