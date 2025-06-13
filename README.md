# adf-http-to-adls-ingestion

ADF pipeline to ingest CSV data from an HTTP source into Azure Data Lake Storage Gen2. This project includes linked services, datasets, and pipelines for automating data ingestion from a public URL to cloud storage.

## Project Structure

```
adf-http-to-adls-ingestion/
│
├── datasets/
│   ├── http_dataset.json
│   └── adls_sink_dataset.json
│
├── linkedServices/
│   ├── http_linked_service.json
│   └── adls_linked_service.json
│
├── pipelines/
│   └── http_to_adls_pipeline.json
│
└── README.md
```

## Assignment Requirement

- Copy the `cases_deaths.csv` file from an HTTP location to Azure Data Lake Gen2 storage using Azure Data Factory.

## Prerequisites

- Azure subscription
- Azure Data Factory instance
- Azure Data Lake Storage Gen2 account

> **Note:** All Azure Data Factory resources (linked services, datasets, pipelines) are exported/imported as JSON files. Place each file in its respective folder as shown in the project structure.

## Source File

- **URL:**  
  `https://raw.githubusercontent.com/PushpakVootla21/Datasets/refs/heads/main/Files/cases_deaths.csv`


> **Note:** All Azure Data Factory resources (linked services, datasets, pipelines) are exported/imported as JSON files.

## Steps

1. **Create Linked Service for HTTP Source**
   - Base URL: `https://raw.githubusercontent.com/`
   - Relative URL: `PushpakVootla21/Datasets/refs/heads/main/Files/cases_deaths.csv`
     - *For other files, update the relative URL accordingly (e.g., change the file name as needed).*
   - Save as `http_linked_service.json`.

2. **Create Linked Service for Azure Data Lake Gen2**
   - Configure connection to your ADLS Gen2 account.
   - Save as `adls_linked_service.json`.

3. **Create Source Dataset**
   - Reference the HTTP linked service and specify the relative URL for `cases_deaths.csv`.
   - Save as `http_dataset.json`.

4. **Create Sink Dataset**
   - Reference the ADLS Gen2 linked service and specify the target container/folder.
   - Save as `adls_sink_dataset.json`.

5. **Create Pipeline**
   - In Azure Data Factory, create a new pipeline.
   - Add a **Copy Data** activity to the pipeline canvas.
   - **Name the activity:** `Copy_HTTP_to_ADLS`
   - Set the **Source** to the HTTP dataset (`http_dataset.json`).
   - Set the **Sink** to the ADLS Gen2 dataset (`adls_sink_dataset.json`).
   - Configure any necessary mappings or settings as required.
   - Save the pipeline as `http_to_adls_pipeline.json`.

6. **Debug the Pipeline**
   - Trigger a debug run to verify the data is copied successfully.

## Usage

1. Import the JSON files into your Azure Data Factory workspace.
2. Update connection strings and credentials as needed.
3. Run the pipeline to ingest data from the HTTP source to ADLS Gen2.

## References

- [Azure Data Factory Documentation](https://docs.microsoft.com/en-us/azure/data-factory/introduction)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction)
- [ADF Copy Activity](https://docs.microsoft.com/en-us/azure/data-factory/copy-activity-overview)