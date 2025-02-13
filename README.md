# PRIDE-Mod Library

[![Build Status](https://travis-ci.org/PRIDE-Utilities/pride-mod.svg?branch=master)](https://travis-ci.org/PRIDE-Utilities/pride-mod)

PRIDE Modification library (PRIDE-Mod) is a Java API to handle post-translational modifications (PTMs) in proteomics experiments. The library provide a common representation between different PTMs databases such as [UNIMOD](www.ebi.ac.uk/pride/archive/) , [PSI-MOD](http://www.psidev.info/MOD) and the PRIDE Modification Slim Ontology.

It also provide a the corresponding parsers for UNIMOD and PSI-MOD databases. It can be use to retrieve an specific modification using Accessions, Amino Acids, Delta Masses (monoisotopic or average). 

# License

pride-mod is a PRIDE API licensed under [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.txt).

# How to cite it:

Perez-Riverol, Y., Wang, R., Hermjakob, H., Müller, M., Vesada, V., & Vizcaíno, J. A. (2014). Open source libraries and frameworks for mass spectrometry based proteomics: A developer's perspective. Biochimica et Biophysica Acta (BBA)-Proteins and Proteomics, 1844(1), 63-76. [PDF File](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3898926/) [Pubmed Record](http://www.ncbi.nlm.nih.gov/pubmed/23467006)

# Main Features

* Support UNIMOD and PSI-MOD databases
* Common representation for all kind of modifications.
* Common API to retrieve modifications based on: Accessions, Amino Acids, Delta Masses, etc.
* Retrieve modifications by String patterns in Names or Descriptions.
* Retrieve Group of Modifications based on common Names or Specificity Groups.

# Availability and Version
* Current version is 2.0.0-SNAPSHOT
* The jara library can be download from the [EBI maven repository]( http://www.ebi.ac.uk/intact/maven/nexus/content/repositories/ebi-repo).

# Getting pride-mod

Maven Dependency
If you wish to include pride-mod in your own Java projects, and you use Maven 2, the following snippets could be useful for you:

- Maven 2 repository definition for pride-mod (and for a host of other EBI libraries):
        
        <repository>
            <id>nexus-ebi-repo</id>
            <url>http://www.ebi.ac.uk/intact/maven/nexus/content/repositories/ebi-repo</url>
        </repository>
        <!-- EBI SNAPSHOT repo -->
        <snapshotRepository>
            <id>nexus-ebi-repo-snapshots</id>
            <url>http://www.ebi.ac.uk/intact/maven/nexus/content/repositories/ebi-repo-snapshots</url>
        </snapshotRepository>

- pride-mod dependency snippet:

        <dependency>
            <groupId>uk.ac.ebi.pride.tools</groupId>
            <artifactId>pride-mod</artifactId>
             <version>x.y.z</version>
        </dependency>


# Getting Help

If you have questions or need additional help, please contact the PRIDE Helpdesk at the EBI: pride-support at ebi.ac.uk (replace at with @).

Please send us your feedback, including error reports, improvement suggestions, new feature requests and any other things you might want to suggest to the PRIDE team.

# This library has been used in:

* Côté, R. G., Griss, J., Dianes, J. A., Wang, R., Wright, J. C., van den Toorn, H. W., ... & Vizcaíno, J. A. (2012). The PRoteomics IDEntification (PRIDE) Converter 2 framework: an improved suite of tools to facilitate data submission to the PRIDE database and the ProteomeXchange consortium. Molecular & Cellular Proteomics, 11(12), 1682-1689. [PRIDE Converter 2](https://code.google.com/p/pride-converter-2/) 
* Vizcaíno, J. A., Côté, R. G., Csordas, A., Dianes, J. A., Fabregat, A., Foster, J. M., ... & Hermjakob, H. (2013). The PRoteomics IDEntifications (PRIDE) database and associated tools: status in 2013. Nucleic acids research, 41(D1), D1063-D1069. [PRIDE-Archive](http://www.ebi.ac.uk/pride/archive/)

How to use pride-mod
===============

# Using pride-mod
 
Here we will show you how to use the PRIDE-Mod library:
   
 * How to retrieve all modifications in PSI-Mod and UNIMOD with 'phospho' pattern in the Description:

   ```java
    ModReader modReader = ModReader.getInstance();
   List<PTM> ptms = modReader.getPTMListByPatternDescription("Phospho");
   assertTrue("Number of PTMs with Term 'Phospho' in name:", ptms.size() == 102);
   ```
 * Retrieve the the UNIMOD modification with Accession 1:
   
   ```java
    File inputFile = new File("unimoddatabase.xml");
    unimodDataAccessController = new UnimodDataAccessController(inputFile);
    PTM ptm = unimodDataAccessController.getPTMbyAccession("UNIMOD:1");
    assertTrue("Difference mass for Average mass is:", ptm.getAveDeltaMass() == 42.0367);
   ```
