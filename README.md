iobatch
=======

AWS Stacks for Batch Processing with I/O to S3 Buckets

[![Lint](https://github.com/dceoy/iobatch/actions/workflows/lint.yml/badge.svg)](https://github.com/dceoy/iobatch/actions/workflows/lint.yml)

Installation
------------

1.  Check out the repository.

    ```sh
    $ git clone git@github.com:dceoy/iobatch.git
    $ cd iobatch
    ```

2.  Install [Rain](https://github.com/aws-cloudformation/rain) and set `~/.aws/config` and `~/.aws/credentials`.

3.  Set a Slack client on AWS Chatbot and get the Slack workspace ID.

4.  Deploy stacks for Amazon GuardDuty. (optional)

    i.    Create IAM roles for administration and execution of CloudFormation StackSets.

    ii.   Create a StackSet for all available regions using `cloudformation/global/guardduty.yml`.

    iii.  Deploy a Chatbot stack for GuardDuty.

    ```sh
    $ rain deploy cloudformation/global/chatbot.yml global-chatbot
    ```

5.  Deploy stacks for user groups. (optional)

    ```sh
    $ rain deploy cloudformation/user/iam.yml user-iam
    ```

6.  Deploy stacks for batch environments.

    ```sh
    $ rain deploy cloudformation/iobatch/s3.yml iobatch-prd-s3
    $ rain deploy cloudformation/iobatch/vpc.yml iobatch-prd-vpc
    $ rain deploy cloudformation/iobatch/iam.yml iobatch-prd-iam
    $ rain deploy cloudformation/iobatch/batch.yml iobatch-prd-batch
    ```

7.  Deploy a Chatbot for AWS Step Functions. (optional)

    ```sh
    $ rain deploy cloudformation/iobatch/chatbot.yml iobatch-prd-chatbot
    ```
