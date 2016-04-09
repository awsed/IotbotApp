This is an android app to control the IoTbot: https://github.com/edlima/iotbot

The app controls the robot movements via AWS IoT as well as retrieves the images taken by the robot camera from an S3 bucket.

You'll need a Cognito Unatuthenticated Role with teh following Inline Policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "mobileanalytics:PutEvents",
                "cognito-sync:*"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::<bucket>/*",
                "arn:aws:s3:::<bucket>"
            ]
        }
    ]
}
```

And the AWSIoTFullAccess policy attached as Managed Policy.

After executing the app for the first time and clicking on the CONNECT button, a new certificate will be created on the AWS IoT console (https://console.aws.amazon.com/iot/home). The certificate needs to be attached with the IoT thing and the IoT policy. 
