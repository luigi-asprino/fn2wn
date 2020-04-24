# Framester's FrameNet to WordNet mappings

This repository contains the Framester's FrameNet 1.5 to WordNet 3.0 mappings organized in three mapping profiles:

1. **Base Profile (B).**  A set of base-mappings was produced by deeply revising existing FrameNet-WordNet mappings (i.e. [eXtended WordFrameNet](https://adimen.si.ehu.es/web/WordFrameNet)),  enriching them with new ones, and manually curating them to rectify mapping errors and evocations.


2. **Direct Profile(D).** The Base Profile plus extensions were automatically added based on:
    - WordNet hyponymy relations between noun and verb synsets, where each frame is extended with direct hyponyms of the noun or verb synsets mapped to frames in the Framester Base dataset.
    - "Instance-of" relations between WordNet noun synsets.
    - Adjective synset similarity.
    - Same verb groups including verb synsets.
    - Pertainymy relations between adverb synsets and noun or adjective synsets.
    - Participle relations between adjective and verb synsets.
    - Morphosemantic links between adjective and verb synsets.
    
    
3. **Transitive Profile (T).** The Direct Profile plus extension automatically added based on:
    - Transitive WordNet hyponymy relations.
    - Unmapped siblings of mapped noun or verb synsets.
    - Derivational links between different kinds of synsets.


The directory **w3id** contains the mappings defined following the current Framester's URI schema, while the directory **backwardCompatibiltyVersion** contains the mappings that follows the old Framester's URI schema.

**Reckless extension**: The reckless extension uses an heuristic in order to extend base mappings with synset's direct hyponym.


### Mapping implementation

The mapping between FrameNet's frames and WordNet's synsets is implemented by using ``skos:closeMatch`` property as follows:

```
<FRAME_URI> skos:closeMatch <SYNSET_URI>
```

### Statistics 

||Number of mappings|
|-|-|
|Base Profile|9337|

||Number of conservative mappings|Number of reckless mappings|
|-|-|-|
|Direct Profile|58250|69824|
|Transitive Profile|146795|214746|

#### Number of mappings per synset

In this section we provide the statistics among the mapped synsets (i.e. here we do not consider the unmapped synsets).

|Profile|Max mappings per synset|Avg. of mappings per synset|
|-|-|-|
|Base|6|1.15|
|Direct Conservative|11|1.29|
|Direct Reckless|14|1.55|
|Transitive Conservative|17|1.52|
|Transitive Reckless|21|2.23|

To compute the average we used the following query

```[SPARQL]
SELECT (MAX(?c) AS ?max) (AVG(?c) AS ?avg){
	SELECT (COUNT(?fn) AS ?c) {
		?fn  skos:closeMatch ?wn
	} GROUP BY ?wn
}
```

## License

- This datset is distributed under licence [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Authors

- [Aldo Gangemi](mailto:aldo.gangemi@cnr.it) (main contributor)
- [Luigi Asprino](mailto:luigi.asprino@istc.cnr.it) (maintainer)
