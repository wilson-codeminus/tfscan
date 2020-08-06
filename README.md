# tfscan

Inspect Terraform resources in a state and plan JSON files

## Install

Using go:

```bash
git clone https://github.com/wilson-codeminus/tfscan.git
cd tfscan
go install
```

Or downloading the binary for a particular [release](https://github.com/wilson-codeminus/tfscan/releases).

## Use examples

### Reading from `terraform` stdout

Command:

```bash
terraform show -json | tfscan
```

Output:

```bash
root_module:
├─ google_app_engine_application.default
├─ google_project_iam_member.datastore_import_export_admin["serviceAccount:service01@project-example.iam.gserviceaccount.com"]
├─ google_project_iam_member.datastore_user["serviceAccount:service01@project-example.iam.gserviceaccount.com"]
├─ google_project_iam_member.logging_config_writer["serviceAccount:service02@project-example.iam.gserviceaccount.com"]
├─ google_project_iam_member.spanner_admin["serviceAccount:service01@project-example.iam.gserviceaccount.com"]
├─ google_project_iam_member.storage_admin["serviceAccount:service01@project-example.iam.gserviceaccount.com"]
├─ google_project_iam_member.storage_admin["serviceAccount:project-example@appspot.gserviceaccount.com"]
├─ google_project_service.default["spanner.googleapis.com"]
├─ google_project_service.default["datastore.googleapis.com"]
├─ google_project_service.default["appengine.googleapis.com"]
├─ google_project_service.default["storage.googleapis.com"]
├─ google_project_service.default["storage-component.googleapis.com"]
├─ google_storage_bucket.default["bucket01"]
├─ google_storage_bucket.default["bucket02"]
├─ google_storage_bucket.default["bucket03"]
├─ module.project:
│  ├─ google_project.default
│  ├─ google_project_iam_audit_config.audit_config
│  ├─ google_project_iam_member.owner
│  ├─ module.project.module.log_exporter:
│  │  ├─ google_bigquery_dataset.dataset
│  │  ├─ google_logging_project_sink.sink
│  │  ├─ google_project_service.bigquery
```

## Listing all unique resource types from a Terraform state JSON file

Command:

```bash
tfscan -json state.json -types
```

Output:

```bash
google_app_engine_application
google_bigquery_dataset
google_logging_project_sink
google_project
google_project_iam_audit_config
google_project_iam_member
google_project_service
google_storage_bucket
```
