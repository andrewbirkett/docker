FROM node:12.11.1

RUN apt-get update

RUN npm install -g aws-cdk
RUN npm install @aws-cdk/aws-s3 @aws-cdk/aws-apigateway @aws-cdk/aws-lambda

RUN apt-get -qq -y install python python-pip less 
RUN pip install awscli

