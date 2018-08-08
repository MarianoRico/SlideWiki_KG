# SlideWiki RDF Knowledge Graph 
There is a [cool page](https://marianorico.github.io/SlideWiki_KG) with the content of this document.

This RDF KG is built by means of Morph mappings.


## About Morph
Morph ([Morph-XR2RML](https://github.com/frmichel/morph-xr2rml)) is an implementation of [XR2RML](https://hal.archives-ouvertes.fr/hal-01141686).
XR2RML is an extension of [RML](http://rml.io) (supports MongoDB). 
RML is an extension of [R2RML](http://rml.io/) (does not support MongoDB).
R2RML is a W3C Recommendation.

## Queries
These are a few examples of SPARQL queries that can be run over the SPARQL Endpoint located at http://slidewiki.oeg-upm.net/sparql 

### Q1. My decks (IRIs of decks created by a given user (forename))
Substitute 'Mariano' for any other literal.
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?d WHERE {
   ?u a swo:User .
   ?u swo:hasForename ?n . FILTER (regex(?n, 'Mariano')) .
   ?d a swo:Deck .
   ?d swo:hasUser ?u
}
```

### Q2. My slides (IRIs of slides created by a given user (forename))
Substitute 'Mariano' for any other literal.
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?s WHERE {
   ?u a swo:User .
   ?u swo:hasForename ?n . FILTER (regex(?n, 'Mariano')) .
   ?s a swo:Slide .
   ?s swo:hasUser ?u
}
```

### Q3. Top deck creators (ranking of users by number of decks created)
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?n (COUNT(?d) AS ?count) WHERE {
   ?u a swo:User .
   ?u swo:hasForename ?n .
   ?d a swo:Deck .
   ?d swo:hasUser ?u
} GROUP BY ?n ORDER BY DESC(?count)
```

### Q4. Top slide creators (ranking of users by number of slides created)
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?n (COUNT(?s) AS ?count) WHERE {
   ?u a swo:User .
   ?u swo:hasForename ?n .
   ?s a swo:Slide .
   ?s swo:hasUser ?u
} GROUP BY ?n ORDER BY DESC(?count)
```

### Q5. slideRevision(s) more used (in more deckRevisions)
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?sr (COUNT(?sr) AS ?count) WHERE {
   ?sr a swo:SlideRevision .
   ?sr swo:inDeckRevision ?dr .
   ?dr a swo:DeckRevision 
} GROUP BY ?sr ORDER BY DESC(?count)
```

### Q6. SlideRevisions with a given content 
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?sr WHERE {
   ?sr a swo:SlideRevision .
   ?sr swo:content ?c . FILTER (regex(?c, 'Semantic Web')) .
} 
```

### Q7. SlideRevisions created after a given date (timestamp means created)
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?sr WHERE {
   ?sr a swo:SlideRevision .
   ?sr swo:timestamp ?n . FILTER (?n > "2018-07-17T00:00:00Z"^^xsd:dateTime) .
} 
```


# Summary of markdown syntax
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

