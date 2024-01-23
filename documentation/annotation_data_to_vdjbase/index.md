# AIRR-seq Data Transfer Tool

## Description

This script facilitates the transfer of annotation data to the AIRR-seq directory of a local repository. The primary function is to automate the population of project-specific directories with the required annotation data, metadata, and file structures.

## GitHub
  [GitHub](https://github.com/yaarilab/Annotation_to_VDJbase) repository

## Features

- Verification of existing directory structures.
- Validation of `airr_correspondence.csv` to ensure consistency with the project's data.
- Mapping of VDJbase project identifiers with AIRR-seq repertoire IDs.
- Verification of annotation presence within the sequence data store.
- Consolidation of metadata from various sources.
- Transfer of essential annotation files, including haplotype and genotype files, and OGRDB reports.

## Prerequisites

- The repository must be previously cloned to the local disk.
- The directory structure within the repository should be set up according to the expected AIRR-seq format.


### Overview of the Script's Functionality:

- **Verification of Directories**: Initially, the script checks to confirm that the source directory (where the annotation files are located) and the target repository directory (where the files will be copied to) exist. This step prevents any file transfer errors due to incorrect or non-existent file paths.

- **airr_correspondence.csv Validation**: This is a crucial validation step where the script ensures that the `airr_correspondence.csv` file exists within the target repository. It then checks this file for references matching the project name in the `airr_file` column to maintain data integrity between the sequence data store and the repository.

- **Mapping Project Data**: The script extracts the mapping between the VDJbase project identifiers and the AIRR-seq repertoire IDs. It parses the project's naming conventions (e.g., Pn_In_Sn, where Pn is the project number, In is the individual identifier, and Sn is the sample number) to establish a relationship between internal project IDs and the corresponding annotation data.

- **Annotation Verification**: Before proceeding with the file transfer, the script checks the sequence data store to confirm the existence of annotation files for each listed `airr_repertoire_id`. If any annotations are missing, the script halts execution and alerts the user, ensuring that incomplete data is not transferred.

- **Metadata Consolidation**: The script builds consolidated metadata by merging data from the repertoire metadata with any additional metadata found in the 'preprocessed' and 'annotated' directories within the sequence data store. This consolidated metadata is then stored both in the sequence data store and the target repository directory.

- **File Copying**: Following metadata consolidation, the script copies the required files (haplotype files, genotype files, and OGRDB reports) for each sample from the annotation directory to the corresponding samples directory in the target repo. It adheres to the existing directory structure and naming conventions used within the repository.

## Setup

1. Clone the repository to your local machine.
   ```bash
   git clone <repository-url>
   ```
2. Navigate to the cloned repository directory.
3. Ensure the target directory structure follows the required AIRR-seq format (e.g., `digby_data\AIRR-seq\Human\IGK\samples\P1`).

## Usage

To run the script, you need to pass the following arguments:

- `project_name`: The name of the project (e.g., `PRJNA300878`).
- `source_folder`: The folder from which to copy annotation data (e.g., `../sequence_data_store/PRJNA300878/current`).
- `metadata_filename`: The path to the repertoire metadata file (e.g., `../sequence_data_store/PRJNA300878/project_metadata/metadata.json`).
- `target_repo_path`: The path to the target repository directory (e.g., `digby_data\AIRR-seq\Human\IGH`).

Run the script from the command line by navigating to the directory containing the script and executing the following command:

```bash
python Annotation_to_VDJbase.py <project_name> <source_folder> <metadata_filename> <target_repo_path>
```


## Troubleshooting

If the script encounters errors, it will print an error message to the console. Common issues may include missing directories, files, or discrepancies in the `airr_correspondence.csv`. Ensure all prerequisites are met and the paths are correctly specified.

---

