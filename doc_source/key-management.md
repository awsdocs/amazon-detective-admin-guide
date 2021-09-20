# Key management for Amazon Detective<a name="key-management"></a>

Because Detective does not store any personally identifiable customer data, it uses AWS managed keys\.

This type of KMS key can be used across multiple accounts\. See the [description of AWS owned keys in the AWS Key Management Service Developer Guide](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#aws-owned-cmk)\.

This type of KMS key rotates automatically every three years \(1095 days\)\. See the [description of key rotation in the AWS Key Management Service Developer Guide](https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html)\.