# Huawei Cloud - Cross Region OBS Migration – Solution




Migrating large amount of data across regions is very demanding in terms of costs and time. In order to migrate OBS objects from Region_A to Region_B, we have the following solutions
- Object Storage Migration Service (OMS) –  is an online data migration service that helps you quickly, easily, and securely move object data to Huawei Cloud Object Storage Service (OBS).
- obsutil – Command line tool for accessing and managing OBS on Huawei Cloud. 
- Data Express Service (DES) – TB-scale data transmission service. It provides physical storage devices (such as Teleport, external USB hard disks, SATA disks, and SAS disks) to transmit terabytes of data to Huawei Cloud
- Software development kits (SDKs) – Developers can directly use API functions provided by OBS SDKs to obtain the OBS service capabilities
- Cross Region OBS Migration Solution – This document presents a solution used by HWC customers that are interested on reducing the migration cost & time by compressing files before migrating


---
# Existing Solutions – Comparison

![image](https://github.com/davira/cross_region_obs_migration/assets/8401868/123f8ee6-c72a-4865-bffb-3335455c7038)


---
# All command line arguments


| Argument Command           | Value                    | Default                      | Description                                                                                                                                                                                   |
|----------------------------|--------------------------|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -h, --help                 | None                     | False                        | Show this help message and exit                                                                                                                                                               |
| execution_type             | execution_type           | None                         | Use 'source' if script runs on ECS in same region as Source Bucket. Use 'destination' if runs on ECS in same region as Destination Bucket ["source", "destination", "source_and_destination"] |
| --clean_mode               | clean_mode               | False                        | True if you want to delete intermediate compressed files that have been successfully migrated, once migration finish                                                                          |
| --thread_mode              | thread_mode              | True                         | True if you want to use multiple threads to speed up (high CPU usage)                                                                                                                         |
| --has_encrypted_bucket     | has_encrypted_bucket     | True                         | If source or destination buckets are encrypted, we can NOT compare the MD5 using ETAG, therefore, we can only compare with size                                                               |
| --display_statistics       | display_statistics       | True                         | Show migration statistics (estimation)                                                                                                                                                        |
| --max_files_transfer       | max_files_transfer       | 0                            | Maximum files to transfer (mostly used for testing purposes).  Zero (0, default) means all                                                                                                    |
| --source_ak                | source_ak                | SET_SOURCE_AK                | Source account AK                                                                                                                                                                             |
| --source_sk                | source_sk                | SET_SOURCE_SK                | Source account SK                                                                                                                                                                             |
| --source_region            | source_region            | SET_SOURCE_REGION            | Source account region (e.g.   ap-southeast-2) https://developer.huaweicloud.com/intl/en-us/endpoint?OBS                                                                                       |
| --source_bucket_name       | source_bucket_name       | SET_SOURCE_BUCKET_NAME       | Source Bucket Name (without   obs://)                                                                                                                                                         |
| --source_dir_path          | source_dir_path          | SET_SOURCE_DIR_PATH          | Source root path                                                                                                                                                                              |
| --intermediate_ak          | intermediate_ak          | SET_INTERMEDIATE_AK          | Intermediate account AK                                                                                                                                                                       |
| --intermediate_sk          | intermediate_sk          | SET_INTERMEDIATE_SK          | Intermediate account SK                                                                                                                                                                       |
| --intermediate_region      | intermediate_region      | SET_INTERMEDIATE_REGION      | Intermediate account region   (e.g. ap-southeast-2) https://developer.huaweicloud.com/intl/en-us/endpoint?OBS                                                                                 |
| --intermediate_bucket_name | intermediate_bucket_name | SET_INTERMEDIATE_BUCKET_NAME | Intermediate Bucket Name   (without obs://)                                                                                                                                                   |
| --intermediate_dir_path    | intermediate_dir_path    | SET_INTERMEDIATE_DIR_PATH    | Intermediate root path                                                                                                                                                                        |
| --destination_ak           | destination_ak           | SET_DESTINATION_AK           | Destination account AK                                                                                                                                                                        |
| --destination_sk           | destination_sk           | SET_DESTINATION_SK           | Destination account SK                                                                                                                                                                        |
| --destination_region       | destination_region       | SET_DESTINATION_REGION       | Destination account region (e.g.   ap-southeast-2) https://developer.huaweicloud.com/intl/en-us/endpoint?OBS                                                                                  |
| --destination_bucket_name  | destination_bucket_name  | SET_DESTINATION_BUCKET_NAME  | Destination Bucket Name (without   obs://)                                                                                                                                                    |
| --destination_dir_path     | destination_dir_path     | SET_DESTINATION_DIR_PATH     | Destination root path                                                                                                                                                                         |
