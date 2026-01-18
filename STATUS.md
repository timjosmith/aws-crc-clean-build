## Current state

- Repository initialised with clean structure and licensing
- CloudFormation template managed in version control
- GitHub Actions configured with OIDC (no static AWS credentials)
- Dedicated IAM deployment role scoped to repository and main branch
- S3 bucket successfully deployed via CloudFormation
- CloudFront distribution deployed via CloudFormation using a private S3 origin and Origin Access Control
- CloudFront lifecycle validated (create → delete → redeploy)
- Stack lifecycle validated (deploy → delete → redeploy)

