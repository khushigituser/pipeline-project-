  🚀 Azure Data Factory Project: Automated Country Data Pipeline

This project is built using Azure Data Factory (ADF) and automates the process of fetching, processing, and storing country-level data. 



*Project Overview*

This pipeline performs the following:

FetchCountryData Pipeline: Takes a list of country names as input, fetches their public API data (like population, capital, etc.) using a ForEach loop and stores each as an individual .json file.

CopyCustomerPipeline: Executes conditional data movement from a database to Azure Blob Storage only if customer count exceeds a specified threshold.

CopyProductPipeline: Transfers product data from on-prem SQL Server to the cloud.



*Key Features*

✅ Parameterization — Dynamic country list input and file naming using @dataset().FileName

🔁 Looping with ForEach — API call for each country in a parameterized loop

💾 Blob Storage Output — JSON files saved to countrydata/ container

🧪 Condition-based Copy — Data copied only when row count condition is met

🕒 Triggering — Custom trigger runs the customer pipeline twice a day (12 AM & 12 PM IST)

🔄 GitHub Integration — CI-ready version-controlled pipelines stored under /mainbranch


*Repo Structure*

pipeline-project/
│
├── dataset/                # JSON datasets (source & sink)
├── pipeline/               # Pipelines like CopyCustomerPipeline, FetchCountryData
├── linkedService/          # AzureBlobStorageLS & DB connections
├── trigger/                # trigger1.json for twice-daily schedule
├── publish_config.json     # ADF publish branch config
└── readme.md               # This file 


*Technologies Used*

☁️ Azure Data Factory

💾 Azure Blob Storage

🧮 SQL Database (Azure / Local)

🔁 REST APIs (for country data)

🌐 GitHub for source control & versioning


*How It Works*

1. Run the FetchCountryData pipeline with parameters:

["India", "Canada", "Japan", "Russia", "UK"]

2. The API calls are executed inside a ForEach loop.

3. Files are saved as india.json, canada.json, etc. in your countrydata container.

4. Trigger CopyCustomerPipeline to run only if records > 500 — checked dynamically.

5. Schedule this with trigger1 to automate twice-daily runs.


Future Improvements

1. Enable failure alerts via email or Logic Apps

2. Archive old files on a monthly basis

3. Add more APIs (e.g., weather, economy) to enrich data



*Screenshots*

![Screenshot 2025-07-05 143718](https://github.com/user-attachments/assets/ac1e8cfd-ef54-4f30-9d78-003407ea6097)
![Screenshot 2025-07-05 143912](https://github.com/user-attachments/assets/1321d9c0-68e3-4873-a5f0-ca5abdb10a61)
![Screenshot 2025-07-05 143934](https://github.com/user-attachments/assets/9f6a83db-5b92-477c-805d-41a0a814be98)



*Author*

🔗khushigituser

Feel free to fork, clone, or drop a ⭐ if you find this useful.
