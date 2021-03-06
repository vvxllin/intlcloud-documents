CAM provides the following features:
	
### Access Permission Management

A sub-account can be created under a root account and granted the management permissions of the resources there, without having to share the root account's identity credentials.

### Refined Permission Management

CAM allows you to use permissions to control who can access what kind of Tencent Cloud resources and services at a granular level. For example, you can grant some sub-accounts read permissions for a specific COS bucket, and other sub-accounts write permissions for a specific COS object. Resources and access permissions can be granted in batches.

### Federated Identity

Users who get passwords through CAM by using your existing identity verification system (for example, your enterprise network or through an Internet identity provider) can obtain temporary access permissions to your Tencent Cloud account.

### Data integrity

CAM is now available in Tencent Cloud in multiple regions, which allows you to synchronize cross-region data simply through replicating policy data. Although the modified CAM policies will be submitted immediately, the cross-region policy synchronization can result in delayed effects. CAM utilizes cache to improve performance, which may increase the latency in some cases as updates do not take effect until the cache expires.
