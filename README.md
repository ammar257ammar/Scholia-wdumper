## Wikidata graph subsetting for Scholia using Wdumper

This repository contains a project's work about getting a subset form the [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) knowledge graph to run [Scholia](https://scholia.toolforge.org/) on top of it.

In order to take a subset from Wikidata, several approaches are available:

1. SPARQL construct queries (against the Wikidata query service)
2. Graph subsetting using ShEx expressions.
3. [Wdumper](https://wdumps.toolforge.org/) tool to make partial dumps of Wikidata using a JSON specifications file.



In this project, Wdumper was used to create a subset from Wikidata that can be used to run Scholia on top of it.

* Wdumper was dockerized so I could run it on the OpenShift computing platform at Maastricht University (DSRI). Here is the [Wdumper](https://github.com/ammar257ammar/wdumper) Github repository.

* Since this is a pilot project, I used an older dump of Wikidata which dates back to 2014. The size of that dump is 3440MB (3.5GB), while the latest dump of Wikidata is 88GB large.

* The 2014 wikidata dump is available [HERE](https://drive.google.com/uc?id=1JeowPytImF08kch7RJ71g7sHhbPn93MQ&export=download)

* Wdumper needs a JSON file as input beside the dump to specify what needs to be extracted from the dump into the subset. Two main aspects should be provided in the JSON files:
  * **Entities:** the entities that need to be extracted from the dump identified by the provided properties (like having a property or a specific value for the property).
  * **Properties:** the properties that need to be extracted for the selected entities. For example: if we need to get only P31 statements for the entities then we provide P31 to the properties array in the JSON file.

### Results

The subsetting took 32 minutes to complete and the resulted RDF (ntriples) files has a size of **637MB**

The subset is (637/3440) ~= **18%** of the Wikidata full dump