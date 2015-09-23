# Washington DC Office of Campaign Finance - Future API

Data from https://efiling.ocf.dc.gov/ as if it had come from an API.

## Usage

Bypass manual data downloads in favor of making programmatic use of the [.csv](/data/csv) and [.json](/data/json) files in this repository.

## Data Updating

When the data on https://efiling.ocf.dc.gov/ changes, please contribute an update to the data in this repository by following the manual process below.

Do not deviate from the scientific process or make any manual revisions.

If the DC Office of Campaign Finance changes their data portal to a web service or fully-functional API, stop updating this repository and use that instead.

### Data Update Process

Visit https://efiling.ocf.dc.gov/DataDownload in a web browser.

Locate a dropdown menu containing the following `Filer Type` values:

 + Principal Campaign Committee
 + Political Action Committee
 + Initiative
 + Referendum
 + Recall
 + Transition Committee
 + Inaugural Committee
 + Legal Defense Committee
 + Independent Expenditure Committee
 + Exploratory Committee
 + Senators & Representatives
 + Constituent Service Program

##### Downloading Contribution Reports

Notice the default `Type` toggle selection of "Contributions". Make sure this selection stays active during the entirety of this process.

![filer-type-dropdown-menu-screenshot](/images/download-contributions.png)

For each `Filer Type`, execute the following tasks in order:

 1. Select the filer type from the dropdown
 2. Click the Search button, and wait for the resulting data
 3. Click the Export button to export data in .csv format
 4. Move the resulting .csv file into its proper place in this repository.

Store contribution report files in the [contributions](/reports/contributions) directory as **`FILER_TYPE`.csv**.

```` sh
mv ~/Downloads/DownloadDataSearchResult.csv path/to/repo/reports/contributions/`FILER_TYPE`.csv
````

##### Downloading Expenditure Reports

Repeat the process for downloading contributions, except switch the `Type` toggle to "Expenditures" and make sure this selection stays active during the entirety of the process.

![filer-type-dropdown-menu-screenshot](/images/download-expenditures.png)

Store contribution report files in the [expenditures](/reports/expenditures) directory as **`FILER_TYPE`.csv**.

```` sh
mv ~/Downloads/DownloadDataSearchResult.csv path/to/repo/data/expenditures/`FILER_TYPE`.csv
````

##### Converting Reports to Data

Run the report-converter script.

```` rb
ruby lib/convert_reports_to_data.rb
````

##### Versioning the Data

After updating the data on a new branch, submit a pull request for the data updates to be merged into the master branch.

Once data updates are merged into the master branch, create a release tag for future version reference.
