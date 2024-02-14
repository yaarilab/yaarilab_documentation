# ENA Downloader

## Overview

The `EN Downloader` is a Python tool designed to automate the process of downloading sequencing data files from the European Nucleotide Archive (ENA). It fetches FASTQ files associated with a given project ID and organizes them into a specified directory structure

## GitHub
  [GitHub](https://github.com/yaarilab/ENA_download_script) repository

## How It Works

### ENA Downloader.py

This script contains the `ENA Downloader` class, which performs the main functionality of the tool.

#### Class `ENA_Downloader`

- **`find_link` Method:**
  - Fetches the project XML from ENA using the project ID.
  - Parses the XML to find the download link for FASTQ files.

- **`download_file` Method:**
  - Downloads a file from a given URL and saves it to a specified path.

- **`open_metadata` Method:**
  - Opens and reads the project metadata file (JSON format).
  - Extracts and stores important information for each repertoire, such as subject ID, sample ID, and repertoire ID.

- **`download_repertoires` Method:**
  - Downloads the repertoires based on the metadata and the download link found.
  - Organizes the downloaded files into a directory structure based on subject ID, sample ID, and repertoire ID.

- **`start_downloading` Method:**
  - Orchestrates the downloading process by calling other methods in sequence.
  - Handles exceptions that might occur during the process.


## How to Use

1. **Prepare Metadata File:**
   - Ensure that a metadata file in JSON format is present in the project directory. This file should contain information about the repertoires.

2. **Run the Tool:**
   - Use the command line to run `ENA_Downloader_tool.py` with the project name as an argument.
   - Example command: `python ENA_Downloader_tool.py PRJEB12345`
     - Replace `PRJEB12345` with your actual project ID.

3. **Output:**
   - The tool will download and organize the FASTQ files into the specified directory structure within the project directory.
