## He we have the Morph mappings that create the RDF from the SlideWiki mongodb

There is a [cool page](https://marianorico.github.io/SlideWiki_KG) describing this process.

### About Morph
Morph ([Morph-XR2RML](https://github.com/frmichel/morph-xr2rml)) is an implementation of [XR2RML](https://hal.archives-ouvertes.fr/hal-01141686).
XR2RML is an extension of [RML](http://rml.io) (supports MongoDB). 
RML is an extension of [R2RML](http://rml.io/) (does not support MongoDB).
R2RML is a W3C Recommendation.

### Queries
Some SPARQL queries that can be run over the SPARQL Endpoint located at http://slidewiki.oeg-upm.net/sparql 

##
My decks (IRIs of decks created by user U (forename))
```markdown
PREFIX swo: <http://slidewiki.oeg-upm.net/ontology/>
SELECT ?d WHERE {
   ?u a swo:User .
   ?u swo:hasForename ?n . FILTER (regex(?n, 'Mariano')) .
   ?d a swo:Deck .
   ?d swo:hasUser ?u
}
```

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/MarianoRico/SlideWiki_KG/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
