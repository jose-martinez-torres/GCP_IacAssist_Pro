## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0 |
| <a name="requirement_google"></a> [google](#requirement\_google) | >= 4.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_google"></a> [google](#provider\_google) | >= 4.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_bigquery_primary"></a> [bigquery\_primary](#module\_bigquery\_primary) | ./modules/bigquery | n/a |
| <a name="module_cloud_run_primary"></a> [cloud\_run\_primary](#module\_cloud\_run\_primary) | ./modules/cloudrun | n/a |
| <a name="module_gke_primary"></a> [gke\_primary](#module\_gke\_primary) | ./modules/GKE | n/a |
| <a name="module_pub_sub_primary"></a> [pub\_sub\_primary](#module\_pub\_sub\_primary) | ./modules/pubsub | n/a |

## Resources

| Name | Type |
|------|------|
| [google_compute_network.gke_network](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_network) | resource |
| [google_compute_subnetwork.gke_subnet](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_subnetwork) | resource |
| [google_pubsub_topic.primary_topic](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/pubsub_topic) | resource |
| [google_storage_bucket.coldline](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/storage_bucket) | resource |
| [google_storage_bucket.nearline](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/storage_bucket) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_allow_bucket_force_destroy"></a> [allow\_bucket\_force\_destroy](#input\_allow\_bucket\_force\_destroy) | A flag to allow destroying GCS buckets even if they contain objects. Should be false in production. | `bool` | `true` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | The deployment environment (e.g., 'dev', 'test', 'prod'). | `string` | `"test"` | no |
| <a name="input_function_source_bucket_name"></a> [function\_source\_bucket\_name](#input\_function\_source\_bucket\_name) | The GCS bucket where the function's source code zip is stored. | `string` | `"capgemini-accelerator-tfstate"` | no |
| <a name="input_function_source_object_name"></a> [function\_source\_object\_name](#input\_function\_source\_object\_name) | The object name of the function's source code zip. | `string` | `"sample-cloudrun-source-code/source.zip"` | no |
| <a name="input_gcs_location"></a> [gcs\_location](#input\_gcs\_location) | The location for GCS buckets (e.g., a region like 'us-central1' or a multi-region like 'US'). | `string` | `"us-central1"` | no |
| <a name="input_gke_deletion_protection"></a> [gke\_deletion\_protection](#input\_gke\_deletion\_protection) | A flag to enable deletion protection on the GKE cluster. Should be true in production. | `bool` | `false` | no |
| <a name="input_gke_machine_type"></a> [gke\_machine\_type](#input\_gke\_machine\_type) | The machine type for the GKE cluster nodes. | `string` | `"e2-micro"` | no |
| <a name="input_gke_node_count"></a> [gke\_node\_count](#input\_gke\_node\_count) | The number of nodes in the GKE cluster node pool. | `number` | `1` | no |
| <a name="input_name_prefix"></a> [name\_prefix](#input\_name\_prefix) | A prefix used to name all resources (e.g., 'cap-iac'). | `string` | `"cap-iac-accel"` | no |
| <a name="input_project_id"></a> [project\_id](#input\_project\_id) | The GCP project ID where resources will be deployed. | `string` | n/a | yes |
| <a name="input_region"></a> [region](#input\_region) | The primary GCP region for resource deployment. | `string` | `"us-central1"` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_cloud_function_primary_url"></a> [cloud\_function\_primary\_url](#output\_cloud\_function\_primary\_url) | The URL of the primary Cloud Function. |
| <a name="output_coldline_bucket_url"></a> [coldline\_bucket\_url](#output\_coldline\_bucket\_url) | The URL of the Coldline storage bucket. |
| <a name="output_gke_cluster_name"></a> [gke\_cluster\_name](#output\_gke\_cluster\_name) | The name of the primary GKE cluster. |
| <a name="output_nearline_bucket_url"></a> [nearline\_bucket\_url](#output\_nearline\_bucket\_url) | The URL of the Nearline storage bucket. |
| <a name="output_pubsub_primary_topic_name"></a> [pubsub\_primary\_topic\_name](#output\_pubsub\_primary\_topic\_name) | The name of the primary Pub/Sub topic. |
