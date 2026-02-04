## CoralSNP - a Galaxy analysis environment that includes a 30k SNP genotyping array for *Acropora* corals and their dinoflagellate symbionts</h1>

by Greg Von Kuster and Sheila Kitchen

More details provide in: Kitchen SA, Von Kuster G, Kuntz KL, Reich HG, Miller W, Griffin S, Fogarty ND, Baums I. STAGdb: a 30K SNP genotyping array and Science Gateway for Acropora corals and their dinoflagellate symbionts. https://doi.org/10.1101/2020.01.21.914424

### Introduction
<p>This document provides information for using the <a href="https://coralsnp.science.psu.edu/galaxy/" rel="nofollow">Galaxy CoralSNP environment</a>
which is based on the <a href="https://galaxyproject.org/" rel="nofollow">Galaxy workbench</a>.  A general understanding of Galaxy is required, so please spend some time with the <a href="https://training.galaxyproject.org/training-material/topics/introduction" rel="nofollow">introductory tutorials</a> if you are not yet familiar with Galaxy.</p>
<p>The Galaxy CoralSNP environment enables streamlined analysis of the coral SNPchip available from Fisher Scientific to ultimately provide the user with a genet id, converted raw genotyped data, sample relatedness and hybrid status.</p>
<p>The process is straightforward.  Each of the following steps will be discussed in detail in the following sections of this document.</p>
<ul>
<li>A sample metadata file is created by the user from an Excel form template for their samples to be analyzed.  A row is entered into the spreadsheet for each sample, and when finished, the spreadsheet is exported from Excel and saved to disk as a tab-delimited file.</li>
<li>The user logs into the <a href="https://coralsnp.science.psu.edu/galaxy" rel="nofollow">Galaxy CoralSNP environment</a> and creates a new, empty history, ideally naming it in a way that associates it with the run being analyzed.</li>
<li>The user uploads their sample metadata file along with the necessary raw Affymetrix data files into the Galaxy CoralSNP environment using the <em>"Upload file"</em> tool within the <em>"Get Data"</em> section of the Galaxy CoralSNP tool panel (left handside of the window).</li>
<li>The user selects the <em>"Queue genotype workflow"</em> tool from the <em>"Genotype Workflow"</em> section of the Galaxy CoralSNP tool panel, selects the appropriate files as inputs, and executes the tool.  The tool executes the entire analysis for the samples and the user can view the results in the Galaxy history when the analysis is finished.</li>
</ul>

### Create the Sample Metadata File
<p>The metadata file for the run describes the samples being analyzed by providing important information about them.  An Excel Macro template file can be downloaded <a href="https://drive.google.com/file/d/1scdsdcvqBSK57J9KrIkiPWF_vijLWHPa/view?usp=sharing" rel="nofollow">here</a> that can be exported and updated for each run.  Some of the data is optional - here are some details about the columns in the spreadsheet template.</p>
<ul>
<li><strong>user_specimen_id</strong> (required) - user-specific identifier for each sample</li>
<li><strong>field_call</strong> (optional)</li> - species identified in the field
<li><strong>bcoral_genet_id</strong> (optional) - the Baums' lab coral genet id, deprecated but remains for backward compatibility with earlier analyses</li>
<li><strong>bsym_genet_id</strong> (optional) - the Baums' lab symbiont genet id, deprecated but remains for backward compatibility with earlier analyses</li>
<li><strong>reef</strong> (required) - the name of the reef from which the samples were collected</li>
<li><strong>region</strong> (required) - the geographic region in which the reef is located</li>
<li><strong>latitude</strong> (required) - the latitude (in decimal degrees) where the sample was collected</li>
<li><strong>longitude</strong> (required) - the longitude (in decimal degrees) where the sample was collected</li>
<li><strong>geographic_origin</strong> (optional) - how the geographic coordinates are associated with the sample (must be either <em>"colony"</em> or <em>"reef"</em>), defaults to <em>"reef</em>"</li>
<li><strong>colony_location</strong> (optional) - pulldown list includes apical tip, mid-branch, base, sperm, eggs, larva, symbiont, unknown</li>
<li><strong>depth</strong> (optional) - depth (in meters) from surface where the samples was taken, must be decimal value</li>
<li><strong>disease_resist</strong> (optional)- parent colony percent diseased from where the sample was taken</li>
<li><strong>bleach_resist</strong> (optional)- parent colony percent bleached from where the sample was taken</li>
<li><strong>mortality</strong> (optional) - average percent mortality for the genet, if known</li>
<li><strong>tle</strong> (optional)- total linear extension growth estimate (mg/cm2/d), if known </li>
<li><strong>spawning</strong> (optional)- has spawning been observed from this genotype (either <em>"yes"</em> or <em>"no"</em>)?</li>
<li><strong>collector_last_name</strong> (required) - the last name of the collector</li>
<li><strong>collector_first_name</strong> (required) - the first name of the collector</li>
<li><strong>org</strong> (required) - the organization for which the collector is working</li>
<li><strong>collection_date</strong> (required) - the date (format yyyy-mm-dd) when the sample was collected</li>
<li><strong>contact_email</strong> (required) - the collector's email address</li>
<li><strong>seq_facility</strong> (required) - the facility sequencing the samples</li>
<li><strong>array_version</strong> (required) - currently only v 1.0 is available </li>
<li><strong>public</strong> (required) - whether the information about the samples is public, defaults to <em>"Yes"</em></li>
<li><strong>public_after_date</strong> (required) - the date at which information about the samples can be made public, defaults to the current day, a one year hold can be placed on the data</li>
<li><strong>sperm_motility</strong> (optional)- percent sperm motility observed</li>
<li><strong>healing_time</strong> (optional) - average time in days of recovery after intentional wounding or fragmentation </li>
<li><strong>dna_extraction_method</strong> (optional) - method used to extract the sample's DNA</li>
<li><strong>dna_concentration</strong> (optional) - DNA concentration in ng/ul measured with Qubit or PicoGreen </li>
<li><strong>registry_id</strong> (optional)- Coming soon!</li>
<li><strong>result_folder_name</strong> (optional)- provide the folder name of the resuls</li>
<li><strong>plate_barcode</strong> (optional)- provide the plate barcode</li>
</ul>
<p>It is crucial that the information in this sample metadata file is correct since the analysis pipeline will store portions of it in both current and future analyses for comparison and other uses.  The Excel spreadsheet <strong>doesn't</strong> validate the information, so care must be taken when entering the data. To ensure that the data is formatted correctly, the <em>"Validate Affymetrix Metadata"</em> under the <em>"Micro-Array Analysis"</em> section of the Galaxy CoralSNP tool panel can be executed prior to initiating the genotype workflow. </p>
The collector's name, organization and email, reef name, region, etc. should exactly match those entered for previous samples if taken by the same collector, from the same reef, etc.</p>
<p>When the Excel spreadsheet is complete, save the file and the Excel macro will automatically export the information (tab-separated format) into a file called <em>"metadata.txt"</em> in the same folder. This process with overwrite a previous <em>"metadata.txt"</em>, so care should be taken to re-name previous metadata files or create new output folders for each run. It is critical that <em>"metadata"</em> remains in the name of previous file(s). For example, if analyzing Plate 2 data, the file could be named <em>"plate2_metadata.tab"</em>, but any file name that includes the string <em>"metadata</em>" is fine (e.g., <em>"affy_metadata.tabular"</em>).</p>

### Upload the Sample Data to Galaxy CoralSNP for Analysis
<p>You'll have to create an account upon your initial visit to the <a href="https://coralsnp.science.psu.edu/galaxy/" rel="nofollow">Galaxy CoralSNP</a> environment.  General information about registering and logging into Galaxy is available <a href="https://galaxyproject.org/support/account" rel="nofollow">here</a>, and can be leveraged for creating a new account in the Galaxy CoralSNP environment for users that have not yet done so.  If logging in for the first time, a new, empty Galaxy history will be created for you.  If you are logging into an existing account, you should create a new, empty history for the samples you're planning to analyze.  Name the history in a way that associates it with your current samples.</p>
<p>It is imperative that a new analysis is performed within a Galaxy history that contains only the dataset items for the given run.  Analyses should not be performed within a history that contains any items except for the input datasets for the current run.  The analysis pipeline inspects the current Galaxy history and specifies named items as designated inputs to certain tools within the pipeline, so multiple items with the same name will result in pipeline errors.  In addition, all items within the history must be in the <em>"ok"</em> (i.e., <em>"green"</em>) state.  History items in a <em>"queued"</em>, <em>"running"</em> or <em>"error"</em> state will result in analysis errors and cause problems for others attempting to perform analyses.  Problematic items can be deleted from a history by clicking the <em>X</em> icon in the item, allowing for histories to be "cleaned up" in preparation for performing an analysis.  Whenever possible, items being deleted from a history should be <em>"permanently deleted"</em> as this will free up disk space on the Galaxy CoralSNP server.</p>
<p>You can now upload your data for analysis. A general tutorial for uploading data to Galaxy is available <a href="https://training.galaxyproject.org/training-material/topics/galaxy-data-manipulation/tutorials/get-data/slides.html#1" rel="nofollow">here</a>.</p>
<p>Here is a view of the Galaxy upload form that shows all of the files for what was called <em>"Plate 2"</em> of the samples.  Notice that the data type (e.g., <em>"tabular"</em>. <em>"csv"</em>, <em>"txt"</em>, etc) has been selected for each file.  Although not required (Galaxy will auto-detect file formats), this is ideal since it will decrease the time needed to upload all of the data files.  Also notice the names of the files.  With the exception of the <em>"affy_metadata.tabular"</em> file which is named by the user, all of the file names are produced by the Affymetrix sequencing process for the samples.  All of these file names are important - as discussed previously, the analysis pipeline specifies these named files as designated inputs to certain tools within the pipeline.</p>

Raw Affymetrix sample data and samples metadata file for Plate 2:
![alt text](./upload_data.png "Upload Data")

<p>When all of the files have been chosen and the data formats specified, clicking the <em>"Start"</em> button will initiate the upload.</p>

### The Galaxy CoralSNP <em>"Queue genotype workflow"</em> Tool
<p>After uploading the files, select the <em>"Queue genotype workflow"</em> tool from the <em>"Genotype Workflow"</em> section of the Galaxy CoralSNP tool panel.  Here is a view of the tool form and the Galaxy history containing the uploaded Plate 2 sample files.  Notice that the Galaxy history contains only the uploaded files, and that all items are in the <em>"ok"</em> (i.e., <em>"green"</em>) state as discussed previously.  This is essential in order to ensure a successful analysis.</p>

![alt text](./queue_genotype_workflow.png "Queue Workflow")

<p>We mentioned previously that the names of the files are important, and the tool form demonstrates this.  Notice the help text below each input selection (e.g., the word <em>'metadata'</em> must be in the file name</em>).</p>
<p>Executing this tool invokes the entire analysis pipeline consisting of a complex set of processes and components, including three separate <a href="https://galaxyproject.org/learn/advanced-workflow/" rel="nofollow">Galaxy workflows</a>; <em>"EnsureSynced"</em>, <em>"ValidateAffyMetadata"</em> and <em>"CoralSNP"</em>.  The tool shields the complexity of the CoralSNP analysis from the user, and performs its function via the <a href="https://bioblend.readthedocs.io/en/latest/api_docs/galaxy/all.html" rel="nofollow">Galaxy API</a>.</p>
<p>Here is a view of the Galaxy history soon after the tool is executed.  Notice all of the items in the <em>"queued"</em> (i.e., <em>"grey"</em>) state - these are jobs associated with tools in the pipeline that are queued for execution.</p>

![alt text](./qgw_tool_execution.png "Workflow executed")

<p>Executing the <em>"Queue genotype workflow"</em> tool initiates the following tasks:</p>
<ul>
<li>The current history is inspected and the file names of all items are collected.</li>
<li>The public <em>"all_genotyped_samples.vcf"</em> <a href="https://galaxyproject.org/data-libraries/" rel="nofollow">Galaxy data library</a> dataset is located and imported into the current Galaxy history</li>
<li>The <em>"EnsureSynced"</em> Galaxy workflow is located, the appropriate history items are specified as tool inputs, and the workflow is executed.</li>
<li>The results of the <em>"EnsureSynced"</em> workflow are inspected for errors between the <em>"all_genotyped_samples.vcf"</em> and database enteries. If any exist, the analysis is terminated.</li>
<li>The <em>"ValidateAffyMetadata"</em> workflow is located, the appropriate history items are specified as tool inputs, and the workflow is executed.</li>
<li>The results of the <em>"ValidateAffyMetadata"</em> workflow are inspected for errors and if any exist, the analysis is terminated.</li>
<li>The <em>"CoralSNP"</em> workflow is located, the appropriate history items are specified as tool inputs, and the workflow is executed</li>
<li>The <em>"stag"</em> Postgres database is updated with information gathered from the analysis results as the final step of the CoralSNP workflow.</li>
<li>The results of the <em>"CoralSNP"</em> workflow are inspected for errors and if any exist, the analysis is terminated.</li>
<li>The <em>"all_genotyped_samples.vcf"</em> Galaxy data library dataset is updated with information gathered from the analysis results.</li>
</ul>
<p>It is imperative that the previously genotyped samples contained within the <em>"all_genotyped_samples.vcf"</em> dataset are synchronized with the previously genotypes sample records contained within the <em>"stag"</em> database.  The <em>"EnsureSynced"</em> workflow performs this task, ensuring that the data contained within these two components is in sync before allowing the analysis to proceed.</p>
<p>To ensure recovery when necessary, the <em>"stag"</em> database is exported into a backup text file, and a copy of the <em>"all_genotyped_samples.vcf"</em> file is stored before updates occur.  Since both of these components are updated, multiple simultaneous analyses cannot be performed.  The <em>"Queue genotype workflow"</em> tool handles this requirement by ensuring that multiple simultaneous executions are handled serially.  This is done by polling the status of the first execution (by later executions) until it has completed.  Additional simultaneous executions are queued in the order in which they were submitted.  If an analysis ends in an error state with either the <em>"all_genotyped_samples.vcf"</em> dataset or the <em>"stag"</em> database updated so that they are no longer in sync, the backup copy of the appropriate component can be used to replace the problematic on in preparation for the next analysis run.</p>
<p>Here is a view of the CoralSNP workflow, the heart of the Galaxy CoralSNP analysis.</p>

![alt text](./coralsnp_workflow.png "Workflow executed")

<p>As discussed above, the workflow is initialed by the <em>"Queue genotype workflow"</em> tool via the Galaxy API.  The workflow consists of the following tools, all of which can be installed into a local Galaxy environment from the <a href="https://toolshed.g2.bx.psu.edu/" rel="nofollow">Galaxy Tool Shed</a>.</p>
<ul>
<li><em>"Affy2vcf"</em> - converts Affymetrix genotype calls and intensity file to VCF format, available on <a href="https://github.com/freeseek/gtc2vcf/blob/master/affy2vcf.c" rel="nofollow">GitHub</a> </li>
<li><em>"bcftools sort"</em> - sorts BCF/VCF files</li>
<li><em>"bcftools merge"</em> - merges BCF/VCF files</li>
<li><em>"Extract Affymetrix ids for Genotyping"</em> - extracts information from a VCF file that contains Affymetrix identifiers and produces a file that contains a subset of the identifiers combined with additional data to generate the genotype population information for use as input to the <em>"coral_multilocus_genotype"</em> tool</li>
<li><em>"Coral Multilocus Genotype"</em> - renders the unique combination of alleles for two or more loci for each individual, creates report and visualizations </li>
<li><em>"Update Stag Database"</em> - updates the <em>"stag"</em> database tables from a dataset collection where each item in the collection is a tabular file that will be parsed to insert rows into the a table defined by the name of the file</li>
</ul>
<p>The <em>"Coral Multilocus Genotype"</em> tool produces the following outputs:</p>
<ul>
<li><em>"table data"</em> - a collection of tabular datasets used to update the <em>"stag"</em> database, these can generally be ignored</li>
<li><em>"plots"</em> - a collection of PDF datasets that provide visualizations of the analysis, an example of the <em>"percent_breakdown.pdf"</em> is shown below</li>
<li><em>"stag_db_report"</em> - a tabular dataset consisting of important information about the samples</li>
<li><em>"process log"</em> - the tool execution log, this can be inspected in case of errors to help discover causes and how to correct them</li>
</ul>

Example of the % species breakdown results from Plate 2:
![alt text](./multilocus_genotype_results.png "Example Percent Breakdown")
