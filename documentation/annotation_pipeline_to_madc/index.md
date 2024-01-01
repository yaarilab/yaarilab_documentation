# Setting Up the Annotation Pipeline to MADC from GitHub

## Introduction
This guide provides instructions for setting up the Annotation Pipeline to MADC script from its GitHub repository. This script is essential for copying TSV files and merging metadata into the MADC file structure.

## GitHub
  [GitHub](https://github.com/yaarilab/Annotation_pipeline_to_mADC) repository

## Setup Instructions

### Step 1: Cloning the Repository
1. **Open Terminal or Command Prompt**.
2. **Navigate to the desired directory** where you want to clone the repository.
3. **Clone the Repository**:
   - Run the command: `git clone https://github.com/yaarilab/Annotation_pipeline_to_mADC.git`.
   - This will create a local copy of the repository on your machine.

### Step 2: Configuring the Script
1. **Navigate to the Script Directory**:
   - Change directory to the cloned repository: `cd Annotation_pipeline_to_mADC`.
2. **Configure Paths**:
   - Open the script file in a text editor.
   - Modify `STUDIES_PATH` to the directory where MADC studies are stored.
   - Adjust `STUDIES_TO_COPY_PATH` to the directory containing source TSV files and metadata.

### Step 3: Running the Script
1. **Execute the Script**:
   - Run the command: `python annotation_pipeline_to_madc.py`.
2. **Input Study Name**:
   - When prompted, enter the name of the study you wish to process.
   - The script will check for the study's existence and proceed if found.
   - The script is automatically calling the `merge_metadata(project_source, project_dest, tsv_map, pre_processed_map)` function with appropriate parameters. more details can be found [here](./documentation/Merging_Metadata/index.md). 
   - Make sure the study was coppied to the madc file structure.

### Example Terminal Interaction for Cloning and Running
```
$ git clone https://github.com/yaarilab/Annotation_pipeline_to_mADC.git
Cloning into 'Annotation_pipeline_to_mADC'...

$ cd Annotation_pipeline_to_mADC
$ python annotation_pipeline_to_madc.py
Please enter study name, or exit to finish
> PRJNA248411
PRJNA248411 as copied to madc
```
