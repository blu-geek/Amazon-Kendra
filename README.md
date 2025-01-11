
# Creating and Querying Indexes of Several Data Sources with Amazon Kendra

A Media orgnaization has vast amounts of data stored in various systems like SharePoint for internal documents, Salesforce for customer information, and ServiceNow for IT service requests. Valtara offers Machine Learninig and Data Analytics services to this organization and needs to find a specific customer contract stored in SharePoint while also looking up related service tickets in ServiceNow.Performing a single search query with Kendra will pull relevant information from both SharePoint and ServiceNow, providing a unified set of results across these different platforms.

# Amazon Kendra Index


<img width="469" alt="Screenshot 2025-01-10 at 23 30 52" src="https://github.com/user-attachments/assets/8dd096f1-6aec-4918-a6a5-6929f2f18fa2" />



# Activity Guide: Create and Query an Index with Amazon Kendra

1. Set Up the AWS Environment
AWS Account and Prerequisites:
Ensure you have an active AWS account.
Enable billing alerts using AWS CloudWatch to manage costs.
Supported Regions:
Use one of the supported regions (e.g., N. Virginia, Oregon, Asia Pacific (Sydney), Ireland).

2. Create an Amazon Kendra Index
- Access Amazon Kendra Console:
  Log in to the AWS Management Console and search for Amazon Kendra.
- Create Index:
  Click Create an Index and provide the following details:
  Index Name: (e.g., demo-index).
  IAM Role: Create a new role with permissions or use an existing one.
  Choose the Developer Edition for experimentation and proof-of-concept.
  Complete the setup and wait for the index creation (may take 15–30 minutes).

3. Update IAM Role Permissions
- Open IAM Console:
  Search for the IAM role associated with the Kendra index (e.g., AmazonKendra-index-role).
- Attach Policies:
  Add the AmazonS3ReadOnlyAccess policy to grant Kendra access to the S3 bucket.

4. Configure S3 Connector as Data Source
- Add Data Source:
  In the Kendra Console, go to Add Data Sources and select S3.
  Provide the Data Source Name (e.g., sample-data) and link it to your S3 bucket.
- Sync Data:
  Allow the S3 connector to crawl and index the documents in the bucket.
  Wait for the sync process to complete (may take several minutes to hours depending on data size).

5. Add FAQ Data Source
- Prepare FAQ File:
  Use a .csv file format with question-and-answer pairs (e.g., AmazonKendraSampleFAQ.csv).
  Upload the FAQ file to the S3 bucket and note its S3 URL.
- Configure FAQ:
  In the Kendra Console, go to FAQs and click Add FAQ.
  Provide the FAQ Name, select the FAQ file format, and link the S3 URL.
  Assign the IAM role created earlier and complete the setup.

6. Query the Index
- Use Search Console:
  Navigate to Search Indexed Content in the Kendra Console.
-Test Queries:
 Enter sample queries like:
 "What is Amazon Kendra?"
 "How does Amazon Kendra work with other AWS services?"
 Review the results and ensure accurate responses from indexed documents and FAQs.

7. Clean Up Resources
Delete Kendra Index:
In the Kendra Console, select your index and click Delete.
Remove S3 Data:
Delete the S3 bucket or remove unnecessary files to avoid additional charges.
Detach IAM Role Policies:
Detach policies from the IAM role used for Kendra.
