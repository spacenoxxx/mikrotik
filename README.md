# Mikrotik Setup
 


```yaml
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  AgentRole:
    Type: 'AWS::IAM::Role'
    Properties:
      RoleName: UnifiedAgentRole
      AssumeRolePolicyDocument:
        Version: '2012-10-17'
        Statement:
          - Effect: Allow
            Principal:
              Service: ['ec2.amazonaws.com']
            Action: 'sts:AssumeRole'
      ManagedPolicyArns:
        - 'arn:aws:iam::aws:policy/service-role/AmazonEC2ContainerServiceAutoscaleRole'
      Policies:
        - PolicyName: 'AllowCloudWatchPutMetricData'
          PolicyDocument:
            Version: '2012-10-17'
            Statement:
              - Effect: Allow
                Action: 'cloudwatch:PutMetricData'
                Resource: '*'

```
