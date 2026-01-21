## Current state

- Repository initialised with clean structure and licensing
- CloudFormation template managed in version control
- GitHub Actions configured with OIDC (no static AWS credentials)
- Dedicated IAM deployment role scoped to repository and main branch and managed via CloudFormation
- Temporary bootstrap deploy role used to establish CI/CD and then fully removed
- S3 bucket successfully deployed via CloudFormation
- CloudFront distribution deployed via CloudFormation using a private S3 origin and Origin Access Control
- CloudFront lifecycle validated (create → delete → redeploy)
- Stack lifecycle validated (deploy → delete → redeploy)
- S3 bucket policy applied restricting read access to the CloudFront distribution only (OAC + SourceArn condition)
- Direct S3 object access denied; CloudFront access verified using private origin
- Control-plane to data-plane boundary crossed and validated
- ACM certificate issued (us-east-1) and attached to CloudFront
- Custom hostname (crc.timjosmith.com) configured via CloudFront alias
- Route 53 alias record created; HTTPS access verified end-to-end
- DynamoDB visitor counter table created and stable
- DynamoDB Point-in-Time Recovery (PITR) currently pending re-enablement following bootstrap and role handover
