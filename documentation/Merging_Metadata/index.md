# Overview of Python Script for Merging Metadata

This script is automatically invoked as part of starting the [Annotation pipeline to MADC](./documentation/annotation_pipeline_to_madc/index.md). 

## GitHub
  [GitHub](https://github.com/yaarilab/Minimal_ADC/blob/main/app/utils.py) repository

## Purpose

The provided Python script is designed for merging metadata and moving projects files into the madc server environment. Its primary functions are to:

1. **Copy TSV Files:** Transfer TSV files from a server to a minimal ADC file system.
2. **Merge Metadata:** Integrate the original metadata with additional metadata from annotations and pre-processed data, if available.

## Functionality

### 1. Directory Setup and File Copying

- `before_server_loads(config)`: Prepares the environment by creating necessary directories ('log' and 'studies') if they don't exist. It then copies content from a specified source directory to a destination directory, adhering to the ADC structure.

### 2. Metadata Extraction and Merging

- `get_repertoire_details(file_path)`: Extracts key identifiers (repertoire, subject, and sample IDs) from a JSON file.
- `merge_metadata(project_source, project_dest, tsv_map, pre_processed_map)`: Merges various metadata sources into a single JSON file in the destination project directory. It handles both annotated and pre-processed metadata.

### 3. Metadata Update Functions

- `update_annotated_metadata(project_metadata, repertoire_id, annotation_metadata)`: Updates the project metadata with annotated metadata for a specific repertoire.
- `update_pre_processed_metadata(project_metadata, repertoire_id, pre_processed_metadata)`: Similar to the above, but for pre-processed metadata.
- `merge_json_data_recursive(original_data, new_data)`: Recursively merges two JSON objects, ensuring that all relevant data is combined appropriately.

### 4. File Scanning and Organization

- `copy_folder_content(src, dst)`: Manages the copying of TSV files and metadata from the source to the destination, maintaining the ADC structure.
- `find_project_tsv_files(project_path)`, `start_scan(folder_path, folders, pre_processed)`, `scan_subject_folder(subject_path, pre_processed)`, `scan_run_folder(sample_path, pre_processed)`: These functions work together to scan various levels of the directory structure (project, subject, sample, and run levels) to identify and organize TSV files and their corresponding metadata.
- `find_metadata_for_pre_processed(result_path)`, `find_tsv_and_metadata_for_annotated(result_path)`: Locate metadata files for pre-processed and annotated results, respectively.
- `check_result_fileds(result, folder)`: Validates the presence of all required fields in a result.

For testing the merging metadata part, please go to the [Annotation pipeline to MADC](./documentation/annotation_pipeline_to_madc/index.md) document.

For more details, see the [utils.py script on GitHub](https://github.com/yaarilab/Minimal_ADC/blob/main/app/utils.py).