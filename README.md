# dnkg-pilot
Dutch National Knowledge Graph (DNKG) Pilot

A repo to capture the necessary information to build the DNKG via DBpedia cartridges. We use Github prototyping to capture information in files and version them. Once we feel confident that information is complete and things run smooth, we will implement a user interface and better tools.  The structure is very similar to the Databus folder structure. 

## License 
CC-BY - contributions to this repo will be licensed to give attribution to the DBpedia Knowledge Library. 

## Details 
We keep the detailed instructions in this [Google Doc](https://docs.google.com/document/d/19VbocJaTaXDlTtOaO8DgbMDgRQo0OhYwvQ3M7CuRDvs/edit)
 
## View the mapping of Cartridges in our Mapping Viewer Prototype
The sheets were made by [Julio Hernandez](https://github.com/Julio-Noe) 

* We use Google Sheets to aggregate the data: see [Kadaster mapping viewer](https://docs.google.com/spreadsheets/d/e/2PACX-1vQcSEFQa7KosT1CELS0ELTvpUAsXJymKUNf2xiXteYpys-KOSllGDjP9wmM0Vf8NvDkjqEsyIAKgSR1/pubhtml) 
* The Sheets use these sources:
  * this git repo (github.io has a **5 min delay**)
  * [DBpedia Mappings](http://mappings.dbpedia.org/) (no delay)
  * VOID statistics on the raw-export dumps on the Databus (these VOID stats are finished some hours after upload of the dump)
* in each view, two main measures are calculated:
  * impact of a mapping, i.e. when you map one property, it counts how many triples are mapped
  * schema mapping, i.e. how many properties of the schema are mapped
* the **impact measure** is the most relevant as it measures amount of data mapped 
* It follows the pareto-efficiency or 20/80 rule, **mapping up to 80% is the goal**

Below is a list of the available mapping viewers:

- [Kadaster](https://docs.google.com/spreadsheets/d/e/2PACX-1vQcSEFQa7KosT1CELS0ELTvpUAsXJymKUNf2xiXteYpys-KOSllGDjP9wmM0Vf8NvDkjqEsyIAKgSR1/pubhtml)
- [KB](https://docs.google.com/spreadsheets/d/e/2PACX-1vSwhy1BGWl42A-l52iEMYIQUMqzOpCDIxfw2S1blnmjcrXYC94lrQdN1rVS7AA62zzsXjiJ-TV2KL_k/pubhtml#)

## Folder structure

`cartridges/user/source/partition`

where 
  * `user` is the person or organisation producing the data
  * `source` is a short name for the general source of the dataset within that organisation
  * `partition` is a name for the partition generated by `export.construct`. Often a class or category, but arbitrary partitions can be selected in the where clause.
  
## Files 
  * `metadata.ttl` specifies where to acquire the data in a single triple. Note that later the Databus will keep much better metadata and provenance. 
     ```
     @prefix dev: <http://example.com/dev#>.
     <> dev:databusversion <https://databus.dbpedia.org/jj-author/kadaster/bag/2020.07.29> . 
     ```
  * `export.construct` executed over the data to create a partition to be indexed: see [2.4.4. Specify ID space](https://docs.google.com/document/d/19VbocJaTaXDlTtOaO8DgbMDgRQo0OhYwvQ3M7CuRDvs/edit#heading=h.uq0c3d5vz3j8) or look at the examples
  * `links.construct` executed over the data to construct the links 
  * `$dbo-property.pt-construct` 0...n files that export the complex structure described in the where clause, to a flat, coarse-grained DBpedia-like structure in the CONSTRUCT clause

