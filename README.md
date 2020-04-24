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

**Reckless extensions**: The reckless extensions use an heuristic in order to extend base mappings with synset's direct hyponym.

**Specific extensions**:


### Mapping implementation

The mapping between FrameNet's frames and WordNet's synsets is implemented by using ``skos:closeMatch`` property as follows:

```
<FRAME_URI> skos:closeMatch <SYNSET_URI>
```

### Statistics 

In this section we provide the statistics among the mapped synsets (i.e. here we do not consider the unmapped synsets).

|Profile|Number of Mappings|Max mappings per synset|Avg. of mappings per synset|
|-|-|-|-|
|Base|9337|6|1.15|
|Base Specific|9217|5|1.13|
|Direct Conservative|58250|11|1.29|
|Direct Conservative Specific|55597|11|1.23|
|Direct Reckless|69824|14|1.55|
|Direct Reckless Specific|65537|11|1.45|
|Transitive Conservative|146795|17|1.52|
|Transitive Conservative Specific|136097|12|1.41|
|Transitive Reckless|214746|21|2.23|
|Transitive Reckless Specific|190756|18|1.98|

To compute the average we used the following query

```[sparql]
SELECT (SUM(?c) AS ?sum)  (MAX(?c) AS ?max) (AVG(?c) AS ?avg){
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
