
# Private registry authentication

    - URL: https://docs.aws.amazon.com/AmazonECR/latest/userguide/registry_auth.html

    - You can use the AWS Management Console, the AWS CLI, or the AWS SDKs to create and manage private repositories. You can also use those methods to perform some actions on images, such as listing or deleting them. These clients use standard AWS authentication methods. Even though you can use the Amazon ECR API to push and pull images, you're more likely to use the Docker CLI or a language-specific Docker library.

    The Docker CLI doesn't support native IAM authentication methods. Additional steps must be taken so that Amazon ECR can authenticate and authorize Docker push and pull requests.

    The registry authentication methods that are detailed in the following sections are available.


## Using an authorization token

    - An authorization token's permission scope matches that of the IAM principal used to retrieve the authentication token. An authentication token is used to access any Amazon ECR registry that your IAM principal has access to and is valid for 12 hours. To obtain an authorization token, you must use the GetAuthorizationToken API operation to retrieve a base64-encoded authorization token containing the username AWS and an encoded password. The AWS CLI get-login-password command simplifies this by retrieving and decoding the authorization token which you can then pipe into a docker login command to authenticate.

    - To authenticate Docker to an Amazon ECR private registry with the CLI
    To authenticate Docker to an Amazon ECR registry with get-login-password, run the aws ecr get-login-password command. When passing the authentication token to the docker login command, use the value AWS for the username and specify the Amazon ECR registry URI you want to authenticate to. If authenticating to multiple registries, you must repeat the command for each registry.

    - Important
    If you receive an error, install or upgrade to the latest version of the AWS CLI. For more information, see Installing the AWS Command Line Interface in the AWS Command Line Interface User Guide.

    Requirements
    AWS Account ID: 600423610423
    Zone: us-east-2

    * get-login-password (AWS CLI)
    - Template
    $ aws ecr get-login-password --region region | docker login --username AWS --password-stdin aws_account_id.dkr.ecr.region.amazonaws.com

    - Use
    $ aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 600423610423.dkr.ecr.us-east-2.amazonaws.com