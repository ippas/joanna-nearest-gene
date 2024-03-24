# Project title (institute-name-subject)

#### Project logline (technique, organism, tissue type)
Short description of treatment groups/subjects


## Methods
This sections should be a description of preprocessin and analysis ready to be included in the publication


## Preprocessing
Workflow Documentation
1. Importing File with rsIDs to Google Sheet
To begin the process, import the file containing rsIDs into a Google Sheet.

2. Opening VEP Tool
Proceed to open the Variant Effect Predictor (VEP) tool.

3. Copying Column of rsIDs
Copy the column containing rsIDs from your Google Sheet.

4. Using VEP Tool
Navigate to VEP Tool.
Click on "New Job."
Paste the copied input data.
Under Filters, select "Restrict results" and choose "Show one selected consequence per variant."
*For Minor Allele Frequency (MAF):
  Navigate to "Variants and frequency data."
  Select "Frequency data for co-located variants" and choose "1000 Genomes global minor allele frequency."
Click "Run."
Once completed, download the result as result.txt.

5. Changing Result File Name
Rename the downloaded result file to VEP_rsid_(something).txt.

6a. Using merge_snpVep.ipynb (Optional)
If you only need VEP Location for subsequent actions, follow these steps:

Open merge_snpVep.ipynb.
Modify the following variables:
data_path = 'VEP_rsid_(something).txt'
source_path = 'snpList_(something).tsv'
output_file_path = 'output_results_(something).tsv'
Ensure that the column of rsID in source_path is named 'rsID'. If not, update accordingly.

6b. Using snp_vep_location.ipynb (Optional)
If you need VEP Location and Minor Allele Frequency (AF) column, follow these steps:

Open snp_vep_location.ipynb.
Modify the following variables:
data_path = 'VEP_rsid_(something).txt'
source_path = 'snpList_(something).tsv'
output_file_path = 'output_results_(something).tsv'
Ensure that the column of rsID in source_path is named 'rsID'. If not, update accordingly.

7. Running merge_snpVep.ipynb or snp_vep_location.ipynb
Execute the respective notebook based on your requirements.

8. Importing Output to Google Sheet
Import the resulting output_results_(something).tsv file into a Google Sheet.

Choose File -> Import -> Select the output file.
Select the tab as the destination.
Choose separator as TAB and ensure to replace data starting from the selected cell.
Uncheck the option for converting text.

9. Opening findingNearest.ipynb
Open the findingNearest.ipynb notebook.

10. Modifying Variables
Modify the following variables in the notebook:

gtf_file = "Homo_sapiens.GRCh38.110.gtf"
input_file = "output_results_(something).tsv"
output_file = "overlap_results_(something).tsv"
11. Running the Notebook
Execute the notebook with the modified input file.

12. Final Steps
Once completed, the output will be saved as overlap_results_(something).tsv.
Import this file into the Google Sheet next to the existing data, ensuring the rsID column maintains the same order and length as the raw data.

13. Completion
The process is now complete.


## Analysis
Details of analysis

*notes: all files included in the repo need to be referenced, either in README or other .md files. The analysis has to be fully reproducible, in principle the repo should contain code + description of how to run it while data and results kept outside*

## About this template
Directories:
- _root_ - README.md, *.Rproj, general configuration files, etc.
- raw - raw data
- preprocessing - scripts
- data - useful data, created by scripts/tools/preprocessing
- analysis - analysis source code
- results - output ready to present
