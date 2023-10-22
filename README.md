# cs516-cloud-computing

### Oct 20, 2023 
-I bought a domain name and certificate. I also read on ways to connect my domain with Route 53. 

### Oct 21, 2023
-Configured the API Gateway to call the Lambda Function.
-Configured the Lambda function to call SNS. Here's a code snippet for the Lambda function:
```
const AWS = require('aws-sdk');
const sns = new AWS.SNS();
exports.handler = async (event) => {
    const params = {
        Message: 'Hi Milka, sending this from Lambda!',
        Subject: 'Lambda-GET Notification',
        TopicArn: 'arn:aws:sns:us-east-1:863771221714:PortfolioTopic',

    };
    try {
        await sns.publish(params).promise();
        console.log('Message sent to SNS');
    } catch (error) {
        console.error('Error publishing to SNS:', error);
    }

    return {
        statusCode: 200,
        body: JSON.stringify('Message sent to SNS'),
    };
}

```


