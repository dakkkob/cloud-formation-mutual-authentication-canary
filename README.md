
# Cloud Formation Mutual Authentication Canary

This repository contains the CloudFormation template for setting up a canary to monitor a site with mutual authentication.

## Description

The provided AWS CloudFormation template creates a canary which is capable of monitoring a site with mutual authentication. The certificate and key required for the mutual authentication are securely stored in AWS Secrets Manager.

## Parameters

- `UrlToMonitor`: Enter the URL to monitor without "https://".
- `CanaryName`: Unique name of the new canary probe. It must be lowercase and match the regex `^[0-9a-z_\-]+$`.
- `CertificatePublicPart`: Public part of the certificate in PEM format, stored in AWS Secrets Manager.
- `CertificatePrivateKey`: Private key of the client certificate in PEM format, stored in AWS Secrets Manager. This is a sensitive parameter and will not be echoed.

## Resources

The template defines several AWS resources including IAM roles and policies, an S3 bucket for storing canary results, and the canary itself.

The canary is configured to execute a script that leverages AWS SDK to interact with Secrets Manager and fetch the necessary credentials for mutual authentication. It then monitors the specified URL and logs the results.

## Deployment

To deploy this template:
1. Navigate to the AWS CloudFormation console.
2. Create a new stack and upload this template.
3. Fill in the parameter values as required.
4. Review and create the stack.
