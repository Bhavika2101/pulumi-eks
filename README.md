# AWS Golang EKS Cluster
This example creates an AWS EKS Cluster.

## Deploying the App

 To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Install Go](https://golang.org/doc/install)
3. [Configure AWS Credentials](https://www.pulumi.com/docs/intro/cloud-providers/aws/setup/)
4. [Install `aws-iam-authenticator`](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html)
4. [Install `kubectl`](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
### Steps

After cloning this repo, run these commands from the working directory:

1. Create a new stack, which is an isolated deployment target for this example:

    ```bash
    $ pulumi stack init dev
    ```

2. Set your desired AWS region:

    ```bash
    $ pulumi config set aws:region us-east-1 # any valid AWS region will work
    ```

4. Execute the Pulumi program to create our EKS Cluster:

	```bash
	pulumi up
	```

5. After 10-15 minutes, your cluster will be ready and a kubeconfig will be generated.On every environment setup user can save kubeconfig to the $KUBECONFIG path so that all the application can pick the eks cluster.:

    ```bash
    $ pulumi stack output kubeconfig --show-secrets >$KUBECONFIG
    ```

6. Afterwards, destroy your stack and remove it:

	```bash
	pulumi destroy --yes
	pulumi stack rm --yes
	```
