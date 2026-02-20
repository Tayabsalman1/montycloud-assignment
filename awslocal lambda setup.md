## setting up lambda

### making zip
* Ubuntu: ```zip lambda.zip lambda_handler.py```
* Windows: ```Compress-Archive -Path .\lambda_handler.py -DestinationPath .\lambda.zip```

### aws cli for lambda creation
```
#Ubuntu
awslocal lambda create-function \
    --function-name images \
    --runtime python3.12 \
    --timeout 10 \
    --zip-file fileb://lambda.zip \
    --handler lambda_handler.handler \
    --role arn:aws:iam::000000000000:role/lambda-role \
    --environment Variables="{STAGE=local}"
#windows
awslocal lambda create-function `
    --function-name images `
    --runtime python3.12 `
    --timeout 10 `
    --zip-file fileb://lambda.zip `
    --handler lambda_handler.handler `
    --role arn:aws:iam::000000000000:role/lambda-role `
    --environment Variables="{STAGE=local}"
```
### awscli for lambda test
```
#ubuntu
awslocal lambda invoke \
    --function-name images \
    --cli-binary-format raw-in-base64-out \
    --payload '{"key": "value"}' \
    response.json

#windows
awslocal lambda invoke --function-name images outfile.txt
```

