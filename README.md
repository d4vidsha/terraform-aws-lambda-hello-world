# terraform-aws-lambda-hello-world

## Prerequisites

> [!NOTE]
> These prerequisites where taken from the [Terraform AWS Tutorial](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-build#prerequisites).

You will need:

- The [Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) (1.2.0+) installed.
- The [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) installed.
- [AWS account](https://aws.amazon.com/free) and [associated credentials](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html) that allow you to create resources.

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

    Alternatively, you can directly invoke the Lambda function using the AWS CLI bypassing API Gateway. Response is stored in `response.json`.

    ```bash
    aws lambda invoke --region=ap-southeast-2 --function-name=$(terraform output -raw function_name) response.json
    ```

4. To clean up and delete resources, run the following command.

    ```bash
    terraform destroy
    ```

## Additional notes

This project was largely adapted from the [official HashiCorp Terraform tutorials](https://developer.hashicorp.com/terraform/tutorials/aws) on [deploying serverless applications with AWS Lambda and API Gateway](https://developer.hashicorp.com/terraform/tutorials/aws/lambda-api-gateway).

## Resources

- <https://developer.hashicorp.com/terraform/tutorials/aws-get-started>
- <https://registry.terraform.io/providers/hashicorp/aws/latest/docs#authentication-and-configuration>
- <https://developer.hashicorp.com/terraform/tutorials/aws/lambda-api-gateway>
- <https://github.com/github/gitignore/blob/main/Terraform.gitignore>
- <https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html#api-gateway-simple-proxy-for-lambda-output-format>
