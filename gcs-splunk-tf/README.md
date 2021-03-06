# Google Cloud Storage to Splunk Terraform Automation
### Summary
* This template sends the contents of a GCS bucket to Splunk using the HTTP Event Collector (HEC) method. The user provides a GCS bucket on template deployment which will trigger a Cloud Function to send bucket changes to Splunk. A retry Pub/Sub topic and associated retry Cloud Function is included in in this template.

### Prerequisites
* Install [terraform](https://learn.hashicorp.com/terraform/getting-started/install.html)
* Create a GCP Service Account with `Owner`
	* Generate a JSON key for this Service Account and download to an accesible path
	* `export GOOGLE_CLOUD_KEYFILE_JSON={PATH TO SERVICE ACCOUNT JSON KEY FILE}`

### Deployment
* `cd gcs-splunk-tf`
* `terraform init`
* `terraform apply`
	* Provide requested variables when prompted
		* Note: hec_url format is `http(s)://{HOSTNAME}:{PORT}` (Ex. `https://127.0.0.1:8088`)
	* Type `yes` to confirm creation of resources

### Cleanup
* `terraform destroy`
	* Provide requested variables when prompted
	* Type `yes` to confirm deletion of resources
	* See Troubleshooting section below

### Troubleshooting
* In Progress