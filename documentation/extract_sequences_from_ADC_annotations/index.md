# Sequence Data Extraction Script

## Overview

This script is designed to extract sequence data from TSV files located in the ADC annotation tree of a specific project and store them in FASTA format in the ‘preprocessed’ annotation tree of the same project.

## GitHub
  [GitHub](https://github.com/yaarilab/extract_sequences_from_ADC_annotations) repository

## How It Works

- find_all_repertoires(project_name)

This function searches for all `.tsv` files in the `adc_annotated` directory of a given project. It navigates through the directory structure of the project and accumulates the paths of all found TSV files.

- create_preprocessed_structure(project_name, reperoires_paths)

After finding all relevant TSV files, this function creates a `pre_processed` directory within the project's `runs/current` directory. It replicates the subdirectory structure of the source files in the `adc_annotated` directory and calls `extract_zip_file` for each TSV file.

- extract_zip_file(file_path, file_dest_path, file_name)

This function opens each TSV file, reads the data using pandas, and writes the sequences and their IDs into a new FASTA file in the created `pre_processed` directory.

## How to Use

### Running the Script

1. Open a terminal or command prompt.
2. Navigate to the directory where the script is located.
3. Run the script using the following command:

   ```
   python extract_sequences_from_ADC_annotations.py <project_name>
   ```

   Replace `<project_name>` with the name of the project you want to process.

### Command Line Arguments

- `project_name`: (Required) The name of the project whose sequence data you want to process.

