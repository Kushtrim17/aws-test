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
`  --stack-name [APP_NAME] \` <br />
`  --capabilities CAPABILITY_IAM \`<br />
`  --region [REGION_NAME]`<br />


**Example:**

`sam deploy \`<br />
`  --template-file packaged.yaml \`<br />
`  --stack-name sam-app-api \` <br />
`  --capabilities CAPABILITY_IAM \`<br />
`  --region us-west-2`<br />


**SOME USEFUL LINKS**

More about AWS SAM Templates ->[AWS SAM TEMPLATE](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-basics.html)

More about AWS SAM CLI -> [SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-reference.html#serverless-sam-cli)
