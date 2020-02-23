# Contract Testing (Consumer Driven Contracts)

* The aim is to test contracts in isolation. We create a contract and test if server implementation meets the contract. 
We also verify if the contract meets customer requirements.

## Contract

* Contract is sort of an agreement on the communication structure between producer (server) and client(s) (consumer).
* The value of the contract is in the ability to verify BOTH sides of the communication against it.
* We should be able using Contract to generate tests for the Producer (Server) but also we should be able to generate 
stubs (of producer/server) to be used in tests of Client(s).

### Products of a Contract

* Automatically generated tests of the producer (server) that verify it against the Contract.
* For Server tests we want to test only the Contract (API) so we mock the facade and test only HTTP call.
* For Client test we verify if Stub (generated after successful Server contract tests) returns what Client expects and if
client can successfully process retrieved response.

