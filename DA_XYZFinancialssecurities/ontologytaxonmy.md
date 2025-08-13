## 🏦 Mortgage Ontology Taxonomy
### Overview
This ontology defines a semantic structure for representing mortgage-related data, including loans, customers, and applications. It enables interoperability across systems, supports semantic queries, and facilitates integration with linked data platforms.

### 📚 Vocabulary Summary

| Class	| Description |
| :- | :- |
| Loan	| Represents a mortgage loan issued to a customer
| Customer	| Represents an individual applying for or receiving a loan
| Application	| Represents the process of applying for a loan

| Property	| Domain	| Range	| Description |
| :- | :- | :- | :- |
|hasCustomer	| Loan	| Customer	| Links a loan to its customer |
| hasApplication	| Customer	| Application	| Links a customer to their application |
| loanAmount	| Loan	| xsd:decimal	| Specifies the amount of the loan |
| interestRate	| Loan	| xsd:decimal	| Specifies the interest rate |
| applicationDate	| Application	| xsd:date	| Date the application was submitted |

### 🧠 Ontology Taxonomy URI

🔍 Example

<a href="./mortgage_schema.ttl" target="_blank">Mortgage Schema Turtle</a><br/>
<a href="./mortgage_schema.nt" target="_blank">Mortgage Schema N-Triples</a><br/>
<a href="./mortgage_schema.rdf" target="_blank">Mortgage Schema RDF</a>



### 🛠️ Applications

Semantic search and reasoning over mortgage data
Integration with FOAF, schema.org, and other linked vocabularies
Use in RDF stores like Apache Jena, RDF4J, or Blazegraph
Ontology visualization in Protégé