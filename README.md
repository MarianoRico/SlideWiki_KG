# Morph mappings that create the RDF from the SlideWiki mongodb

There is a [cool page](https://marianorico.github.io/SlideWiki_KG) with the content of this document.

## About Morph
Morph ([Morph-XR2RML](https://github.com/frmichel/morph-xr2rml)) is an implementation of [XR2RML](https://hal.archives-ouvertes.fr/hal-01141686).
XR2RML is an extension of [RML](http://rml.io) (supports MongoDB). 
RML is an extension of [R2RML](http://rml.io/) (does not support MongoDB).
R2RML is a W3C Recommendation.

## Queries
Some SPARQL queries that can be run over the SPARQL Endpoint located at http://slidewiki.oeg-upm.net/sparql 

### My decks (IRIs of decks created by user U (forename))
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

# Summary of markdown 

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

