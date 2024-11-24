# Astor X QuixBugs

Hi! This will be the instructions that you need to follow to get the demo of Astor running on bugs from the QuixBugs Dataset.


## Prerequisites

- JDK 11

- macOS/Linux

  **Tip**: Do have a read on Astor's documentation before you proceed, link to the docs is here: [Astor Documentation](https://github.com/SpoonLabs/astor/tree/master), have a read on command line structure and different types of program repair techniques.

## Project Structure



The project directory contains two Maven projects that encapsulates the two bugs from the Quixbugs Dataset. The `evidence_logs` contains previous logs from Astor that has successfully found patches for the bugs. A jar file that contains the latest version of Astor is also included. 

```
. 
├── evidence_logs 
├── KnapSackProject
├── MergeSortProject
└── astor-2.0.0-jar-with-dependencies.jar 
```

## Run

  

Before running Astor, navigate to your maven project of choice and compile it:

```
 mvn clean compile test
```

Afterwards navigate to the root directory where the Astor jar is located and run this command:

```

java -cp astor-2.0.0-jar-with-dependencies.jar fr.inria.main.evolution.AstorMain \
  -mode [REPAIR_TECHNIQUE] \
  -srcjavafolder /src/java/ \
  -srctestfolder /src/test/ \
  -binjavafolder /target/classes/ \
  -bintestfolder /target/test-classes/ \
  -location ~/[ABSOLUTE_PATH_MAVEN_PROJECT] \
  -dependencies [PROJECT_NAME]/lib/* \
  -population 40 \
  -maxgen 10 

```
You will need to replace the `[REPAIR_TECHNIQUE]` with your choice of either `jgenprog` or `jMutRepair`. You will also need to replace the `[ABSOLUTE_PATH_MAVEN_PROJECT]` with the absolute path that points to the Maven project that you want to test. The `[PROGRAM_NAME]` is also needed to be replaced with the chosen project's name. 

Once the command is done, two directories `output_astor` and `diffSolutions` will be automatically generated. 