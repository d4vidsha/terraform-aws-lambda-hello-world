# terraform-aws-lambda-hello-world

## Prerequisites

You will need:

- The [Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) (1.2.0+) installed.
- The [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) installed.
- [AWS account](https://aws.amazon.com/free) and [associated credentials](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html) that allow you to create resources.

> [!NOTE]
> These prerequisites where taken from the [Terraform AWS Tutorial](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-build#prerequisites).

## Running the serverless app

Assuming you have authenticated with the AWS CLI, you can run the following commands to deploy the serverless app.

1. Initialise Terraform.

    ```bash
    terraform init
    ```

2. Apply the Terraform configuration and confirm by typing `yes` when prompted.

    ```bash
    terraform apply
    ```

3. You can now invoke the Lambda via the API Gateway endpoint `/hello`.

    ```bash
    curl "$(terraform output -raw base_url)/hello"
    ```

    Alternatively, you can also directly invoke the Lambda function using the AWS CLI bypassing the API gateway.

    ```bash
    aws lambda invoke --region=ap-southeast-2 --function-name=$(terraform output -raw function_name) response.json
    ```

4. To clean up and delete resources, run the following command.

    ```bash
    terraform destroy
    ```
