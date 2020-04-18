# Framester's FrameNet to WordNet mappings

This repository contains the Framester's FrameNet 1.5 to WordNet 3.0 mappings organized in three mapping profiles:

1. *Base Profile (B).*  A set of base-mappings was produced by deeply revising existing FrameNet-WordNet mappings (i.e. [eXtended WordFrameNet](https://adimen.si.ehu.es/web/WordFrameNet)),  enriching them with new ones, and manually curating to rectify mapping errors and evocations.
2. *Direct Profile(D).* The Base Profile plus extensions were automatically added based on:
  - WordNet hyponymy relations between noun and verb synsets, where each frame is extended with direct hyponyms of the noun or verb synsets mapped to frames in the Framester Base dataset.
  - "Instance-of" relations between WordNet noun synsets.
  - Adjective synset similarity.
  - Same verb groups including verb synsets.
  - Pertainymy relations between adverb synsets and noun or adjective synsets.
  - Participle relations between adjective and verb synsets.
  - Morphosemantic links between adjective and verb synsets.
3. *Transitive Profile (T).* The Direct Profile plus extension automatically added based on:
  - Transitive WordNet hyponymy relations.
  - Unmapped siblings of mapped noun or verb synsets.
  - Derivational links between different kinds of synsets.

The directory *w3id* contains the mappings defined following the current Framester's URI schema, while the directory *backwardCompatibiltyVersion* contains the mappings that follows the old Framester's URI schema.

**TODO** Reckless??


## License

- This package is distributed under licence [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Authors

- [Aldo Gangemi](mailto:aldo.gangemi@cnr.it) (main contributor)
- [Luigi Asprino](mailto:luigi.asprino@istc.cnr.it) (maintainer)
