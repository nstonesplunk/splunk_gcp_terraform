# Retry to Splunk Terraform Automation
### Summary
This template deploys a Cloud Function and a triggering PubSub topic for other Cloud Functions/etc. to use for retrying failed events. The Cloud Function in this template will send events to Splunk using the HTTP Event Collector (HEC) method.

### Prerequisites
* Install [terraform](https://learn.hashicorp.com/terraform/getting-started/install.html)
* Create a GCP Service Account with `Owner`
	* Generate a JSON key for this Service Account and download to an accesible path
	* `export GOOGLE_CLOUD_KEYFILE_JSON={PATH TO SERVICE ACCOUNT JSON KEY FILE}`

### Deployment
* `cd retry-splunk-tf`
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