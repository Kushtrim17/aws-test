# Configure AWS

**1) Open the terminal and run the command** <br />

`aws configure`

<p>Then add all of your personal details</p>

  `AWS Access Key ID` <br />
  `AWS Secret Access Key`<br />
  `Default Region`<br />
  `Default output` -> which can be text or json<br />
  
**More detials can be found [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)**

Next, you have to also install [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)

**A quick start to SAM
[SAM QUICK START](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-quick-start.html)

To run the apps you have to install the dependencies inside the functions(if there is any package.json).

**Then, package the function using SAM**

`sam package \`<br />
`  --output-template-file packaged.yaml \`<br />
`  --s3-bucket [YOUR_BUCKET_NAME]`<br />

**Example:**

`sam package \`<br />
`  --output-template-file packaged.yaml \`<br />
`  --s3-bucket kushtrimsbucket`<br />

**Finally, deploy it**

`sam deploy \`<br />
`  --template-file packaged.yaml \`<br />
`  --stack-name [STACK_NAME] \` <br />
`  --capabilities CAPABILITY_IAM \`<br />
`  --region [REGION_NAME]`<br />


**Example:**

`sam deploy \`<br />
`  --template-file packaged.yaml \`<br />
`  --stack-name sam-app-api \` <br />
`  --capabilities CAPABILITY_IAM \`<br />
`  --region us-west-2`<br />


Sometimes these two commands might not work (I am not sure yet why). In that case use the following [link](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-deploying.html) to package and deploy

`sam deploy --template-file ./packaged.yaml --stack-name [STACK_NAME] --capabilities CAPABILITY_IAM`
##########################################################################################


**SOME USEFUL LINKS**

More about AWS SAM Templates ->[AWS SAM TEMPLATE](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-basics.html)

More about AWS SAM CLI -> [SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-reference.html#serverless-sam-cli)

A great tutorial to develop and test locally using SAM CLI -> [Local Testing and Deployment Best Practices](https://www.youtube.com/watch?v=QRSc1dL-I4U).

AWS SAM CLI Github -> [Github](https://github.com/awslabs/aws-sam-cli)

AWS SERVERLESS EXAMPLE -> [Example](https://github.com/aws-samples/aws-serverless-samfarm)

**SAM BEST PRACTICES**

* Unless function handlers share code, SPLIT THEM into their own independent Lambda functions files or binaries
  * Another option is to USE LANGUAGE SPECIFIC PACAGES to share common code between functions

* Unless independent Lambda functions share event sources, SPLIT THEM into their own code repositories with their own SAM templates

* Locally VALIDATE your YAML or JSON SAM files before committing them. Then do it again in your CI/CD process

**More Best Practices** from minute [39:25](https://www.youtube.com/watch?v=QRSc1dL-I4U)

