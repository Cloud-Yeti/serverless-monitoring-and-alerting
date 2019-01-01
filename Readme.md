# AWS Monitoring and Alerting Solution Service Example

# Youtube link: 
https://www.youtube.com/channel/UCbbp2FFbVQkuFYTJCZ92JQg

## Requirements
- IAM Role with SNS and cloudwatch Access 
- SNS Topic with subsriber that reveives the message
- Lambda function with code that sends sms to a topic
- Cloudwatch event rule that will trigger based off event pattern



## Steps
1) Create the IAM Role
2) Create the SNS Topic
3) Create the Lambda function
4) Create the cloudwatch event rule with event pattern
5) Simulate the event with login/ logout



----
# Deploy this stack with a Cloudformation template we have created.
- Fork/Clone this repo.
- Package the code and package with this command. Make sure to replace the s3 bucket name with a bucket you own 
  ```console
  aws cloudformation package --template-file sendSMSwhenConsoleLogin.yaml --s3-bucket your-s3-bucket --output-template-file output.yaml
  ```
- Deploy the stack with this command. You need to supply the email of the receipient in this command.
  ```console
  aws cloudformation deploy --template-file output.yaml --stack-name console-login-sns-test1 --parameter-overrides         SNSEmailParameter=youremail@gmail.com --capabilities CAPABILITY_NAMED_IAM CAPABILITY_IAM
  ```

- Now check your email for SNS confirmation to confirm subscription.
- Now log out and log back into the AWS Management Console. You should receive an email in a few minutes mentioning the user who logged in as well in the email.

---
## Manual Steps
---
### Create an SNS Topic
![image](https://user-images.githubusercontent.com/22568316/45520223-630b8480-b786-11e8-816e-66442c2a4db9.png)
---

### Confirm SNS email
![image](https://user-images.githubusercontent.com/22568316/50568301-ce6d6800-0d1d-11e9-9dac-c88521e00fdd.png)
 ---


### Create rule
![image](https://user-images.githubusercontent.com/22568316/45520557-e679a580-b787-11e8-98f6-95fb7050b815.png)
---

Logged in - 7:05
Notified- almost immediately

## EMAIL IS SENT 
![image](https://user-images.githubusercontent.com/22568316/45521024-2e99c780-b78a-11e8-8393-2f5ad85ac9e2.png)
---

