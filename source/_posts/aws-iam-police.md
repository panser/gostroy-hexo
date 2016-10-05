---
title: AWS IAM Polices
---
config for add accees by ip adresses and aws login
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "FirstStatement",
      "Effect": "Allow",
      "Principal": {
        "AWS": [
          "$AWS_LOGIN"
        ]
      },
      "Action": [
        "es:*"
      ],
      "Resource": "arn:aws:es:eu-central-1:423995045840:domain/repengine-dev/*"
    },
    {
      "Sid": "SecondStatement",
      "Effect": "Allow",
      "Principal": {
        "AWS": "*"
      },
      "Action": "es:*",
      "Resource": "arn:aws:es:eu-central-1:423995045840:domain/repengine-dev/*",
      "Condition": {
        "IpAddress": {
          "aws:SourceIp": [
            "$IP1",
            "$IP2",
            "$IP3"
          ]
        }
      }
    }
  ]
}
```

for check police [https://policysim.aws.amazon.com/home/index.jsp](https://policysim.aws.amazon.com/home/index.jsp)