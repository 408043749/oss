# Introduction to storage class {#concept_fcn_3xt_tdb .concept}

OSS provides three storage classes: Standard, Infrequent Access \(IA\), and Archive, covering various data storage scenarios from hot data to cold data.

## Standard {#section_r3z_lxt_tdb .section}

OSS Standard storage provides highly reliable, highly available, and high-performance object storage services that support frequent data access. The high-throughput and low-latency service response capability of OSS can effectively support access to hotspot data. Standard storage is ideal for storing various images that are used for social networking and sharing, and storing data for audio and video applications, large websites, and big data analytics.

-   Supported data redundancy mechanisms
    -   Locally redundant storage \(LRS\): uses the data redundancy storage mechanism to store data of each object on multiple devices in the same region, ensuring data durability and availability in case of hardware failure.

        **Note:** Before zone-redundant storage was released, locally redundant storage was the storage mechanism for standard storage.

    -   Zone-redundant storage \(ZRS\): uses the multi-zone mechanism to distribute user data across three zones within the same region. Even if one zone becomes unavailable, the data will still be accessible.
-   Key features
    -   Provides 99.9999999999% \(twelve 9's\) data durability.
    -   Designed to provide 99.995% service availability.
    -   Delivers high-throughput and low-latency access performance.
    -   Supports HTTPS-based transmission.
    -   Supports Image Processing \(IMG\).

## IA {#section_t3z_lxt_tdb .section}

OSS IA storage is suitable for storing long-lived, but less frequently accessed data \(an average of once or twice per month\). IA storage offers a storage unit price that is lower than Standard storage, and is suitable for long-term backup of various mobile apps, smart device data, and enterprise data. It also supports real-time data access. Objects of the IA storage class have a minimum storage duration. Fees occur if you delete objects that are stored for less than 30 days. Objects of the IA storage class have a minimum billable size. Objects smaller than 64 KB are charged as 64 KB. Data retrieval incurs fees.

-   Supported data redundancy mechanisms
    -   Locally redundant storage \(LRS\): uses the data redundancy storage mechanism to store data of each object on multiple devices in the same region, ensuring data durability and availability in case of hardware failure.

        **Note:** Before zone-redundant storage was released, locally redundant storage was the storage mechanism for IA storage.

    -   Zone-redundant storage \(ZRS\): uses the multi-zone mechanism to distribute user data across three zones within the same region. Even if one zone becomes unavailable, the data will still be accessible.
-   Key features
    -   Provides 99.9999999999% \(twelve 9's\) data durability.
    -   Designed to provide 99.995% service availability.
    -   Supports real-time access.
    -   Supports HTTPS-based transmission.
    -   Supports IMG.
    -   Requires a minimum storage duration and minimum billable size.

## Archive {#section_v3z_lxt_tdb .section}

OSS Archive storage has the lowest price among the three storage classes. It is suitable for long-term storage \(at least half a year\) of data that is infrequently accessed. The data may take up to one minute to restore before it can be read. This storage option is suitable for data such as archival data, medical images, scientific materials, and video footage. Objects of the Archive storage class have a minimum storage period. Fees occur if you delete objects that are stored for less than 60 days. Objects of the Archive storage class have a minimum billable size. Objects smaller than 64 KB are charged as 64 KB. Data retrieval incurs fees.

The Archive storage class has the following features:

-   Provides 99.999999999% \(eleven 9's\) data durability.
-   Designed to provide 99.99% service availability.
-   Takes about one minute to restore the data from the frozen state to the readable state.
-   Supports HTTPS-based transmission.
-   Supports IMG, but data needs to be restored first.
-   Requires a minimum storage duration and minimum billable size.

## Comparison of storage classes {#section_uj2_gz1_trv .section}

|Item|Standard|IA|Archive|
|:---|:-------|:-|:------|
|Supported data redundancy mechanisms|LRS and ZRS|LRS and ZRS|N/A|
|Data durability|99.9999999999% \(twelve 9's\)|99.9999999999% \(twelve 9's\)|99.999999999% \(eleven 9's\)|
|Service availability|99.995%|99.995%|99.99% \(restored data\)|
|Minimum billable size of objects|Actual size of objects|64 KB|64 KB|
|Minimum storage duration|No minimum storage duration|30 days|60 days|
|Data retrieval fee|No data retrieval fee|Based on the size of retrieved data. Unit: GB|Based on the size of restored data. Unit: GB|
|Data access|Real-time access with low latency \(within milliseconds\)|Real-time access with low latency \(within milliseconds\)|One minute after data is restored|
|IMG|Supported|Supported|Supported after data is restored|

**Note:** OSS charges a data retrieval fee based on the size of data read from the underlying distributed storage system. The data transmitted over the public network is billed as part of the outbound traffic.

## Supported API operations {#section_pfz_1yt_tdb .section}

|Operation|Standard|IA|Archive|
|:--------|:-------|:-|:------|
|Bucket creation, deletion, and query|
|PutBucket|Supported|Supported|Supported|
|GetBucket|Supported|Supported|Supported|
|DeleteBucket|Supported|Supported|Supported|
|Bucket ACL|
|PutBucketAcl|Supported|Supported|Supported|
|GetBucketAcl|Supported|Supported|Supported|
|Bucket logging|Supported|Supported|Supported|
|PutBucketLogging|Supported|Supported|Supported|
|GetBucketLogging|Supported|Supported|Supported|
|Bucket static website hosting|
|PutBucketWebsite|Supported|Supported|Not supported|
|GetBucketWebsite|Supported|Supported|Not supported|
|Bucket hotlink protection|Supported|Supported|Supported|
|PutBucketReferer|Supported|Supported|Supported|
|GetBucketReferer|Supported|Supported|Supported|
|Bucket lifecycle|
|PutBucketLifecycle|Supported|Supported|Supported for data deletion only|
|GetBucketLifecycle|Supported|Supported|Supported|
|DeleteBucketLifecycle|Supported|Supported|Supported|
|Cross-region replication|Supported|Supported|Supported for restored data|
|PutBucketReplication|Supported|Supported|Supported|
|Cross-origin resource sharing \(CORS\)|
|PutBucketcors|Supported|Supported|Supported|
|GetBucketcors|Supported|Supported|Supported|
|DeleteBucketcors|Supported|Supported|Supported|
|Object operations|
|PutObject|Supported|Supported|Supported|
|PutObjectACL|Supported|Supported|Supported|
|GetObject|Supported|Supported|Supported after data is restored|
|GetObjectACL|Supported|Supported|Supported|
|GetObjectMeta|Supported|Supported|Supported|
|HeadObject|Supported|Supported|Supported|
|CopyObject|Supported|Supported|Supported|
|OptionObject|Supported|Supported|Supported|
|DeleteObject|Supported|Supported|Supported|
|DeleteMultipleObjects|Supported|Supported|Supported|
|PostObject|Supported|Supported|Supported|
|PutSymlink|Supported|Supported|Supported|
|GetSymlink|Supported|Supported|Supported|
|RestoreObject|Not supported|Not supported|Supported|
|Multipart operations|
|InitiateMultipartUpload|Supported|Supported|Supported|
|UploadPart|Supported|Supported|Supported|
|UploadPartCopy|Supported|Supported|Supported|
|CompleteMultipartUpload|Supported|Supported|Supported|
|AbortMultipartUpload|Supported|Supported|Supported|
|ListMultipartUpload|Supported|Supported|Supported|
|ListParts|Supported|Supported|Supported|
|IMG|Supported|Supported|Supported|

