# Maloof Lab Sequencing Database Templates

## Order of filling out a complete database entry

### Prerequisites and notes

1. Convert Excel file to CSV at the time of saving.
2. Delete header row only after upload and making sure the columns align properly
3. If you don’t have data in a column designated as a foreign key, you have to set that cell to NULL by right-clicking on the cell and selecting “Set Field to NULL”. On Window, you can select an entire column.

### Workflow:

1.	In Researcher table, enter first and last name
2.	Fill out Experiment table; note the experiment_id
3.	Fill out Sample table, including Sample_experiment field which should be the same as experiment id __or set to NULL.__
4.	Sample_SRA_organism has to match an existing entry in the Species table __or be set to NULL.__
5.	__Set Sample_library_pool to NULL__
6.	When the library is ready, return to Sample table and fill out information about the library.
7.	When pooling libraries, fill Library_pool table. Note Library_pool_id. Return to Sample table and fill out the Sample_library_pool with Library_pool_id.
8.	When filling out the Data_file table, the file needs to be associated either with an existing pool id in Data_file_pool_id or with an existing sample in Data_file_sample or both or have both fields set to NULL.
9.	Fill out the Analysis table. Note the Analysis_id.
10.	Fill out Mapping_analysis_to_file with the analysis id and the appropriate raw or split data file names from the Data_file table

__Introduction of new species in experiments needs to start from recording the name in the column Species_name in the species table.__

## Naming conventions

* Each variable name starts with the table name followed by an underscore. 
* Each variable that is also present in the SRA metadata includes the SRA variable name preceded by _SRA_. Eg.,[ Table name]_[variable as called by Maloof lab]_SRA_[variable as called by SRA]. In the case where the SRA name is self-explanatory, the field name is shortened to [Table name]_SRA_[variable as called by SRA].
* To identify foreign keys, click on the wrench icon by the table of interest. The foreign keys are listed in a tab at the bottom of the screen (see screen shot below). Any changes to fields serving as foreign keys will require the key to be deleted first. All keys are set to cascade on update and set to NULL on delete. That means that a change to data in a foreign key field will be propagated through the database.

![]ScreenShot1.png
