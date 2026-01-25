## Current state

- Repository initialised with clean structure and licensing.
- CloudFormation template fully managed in version control.
- GitHub Actions configured with OIDC (no static AWS credentials).
- Dedicated IAM deploy role scoped to the repository and main branch, managed via CloudFormation.
- Clear separation between deploy role (control plane) and runtime execution roles to avoid IAM self-mutation.
- Temporary bootstrap execution role used solely for recovery; stack now stable and operating under the standard deploy-role model.

### Frontend infrastructure
- S3 bucket deployed via CloudFormation.
- CloudFront distribution deployed via CloudFormation using a private S3 origin and Origin Access Control (OAC).
- CloudFront lifecycle validated (create → delete → redeploy).
- S3 bucket policy restricts read access to the CloudFront distribution only (OAC with SourceArn condition).
- Direct S3 object access denied; CloudFront access verified using private origin.
- ACM certificate issued in us-east-1 and attached to CloudFront.
- Custom hostname (crc.timjosmith.com) configured via CloudFront alias.
- Route 53 alias record created; HTTPS access verified end-to-end.

### Backend and API
- DynamoDB visitor counter table created and stable.
- DynamoDB Point-in-Time Recovery (PITR) enabled.
- Lambda runtime layer added for the visitor counter slice.
- Dedicated Lambda execution role created with minimal DynamoDB and logging permissions.
- Lambda manually invoked and verified; atomic counter increment confirmed.
- API Gateway (HTTP API) created and integrated with Lambda.
- GET `/count` route deployed with scoped invoke permission.
- Default API stage deployed with auto-deploy enabled.
- CORS explicitly configured for browser access.
- End-to-end path verified: API Gateway → Lambda → DynamoDB.

### Overall
- Stack lifecycle validated (deploy → delete → redeploy).
- All infrastructure remains CloudFormation-managed and fully destroyable.
- Minimal showcase site deployed via CloudFront with JavaScript integration to the visitor counter; end-to-end functionality verified.
