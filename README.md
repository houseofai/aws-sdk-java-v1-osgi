# AWS SDK v1 for Java - OSGI version

The **AWS SDK for Java 1.0 - OSGI version** is a version of the popular Amazon Web Service SDK for Java (v1) turned into OSGI.
It uses the [AWS Bundles project](https://github.com/aws/aws-sdk-java/tree/master/aws-java-sdk-bundle) to shade all AWS projects into one, and include a custom MANIFEST file.

## Getting Started

Before building the project, you might want to get the latest AWS package version. Check on AWS Github repo and the version of the latest build - AWS SDK creates a new build every day, so unless you are looking for a specific feature, leave it like this.

Once you got the AWS SDK version, update the pom.xml with that version:

`<aws.version>1.11.766</aws.version>`

Then you are all set!

### Build the JAR

Simply run:

`mvn clean install`

The build might take a minute or more to download all AWS projects and package it into one JAR.
The build generates a JAR of 205 MB. 

### Deploy the JAR

Get the jar from the repo and deploy it to your OSGI environment.

`.m2/repository/software/amazon/awssdk/aws-sdk-java-v1-osgi/1.11.766/aws-sdk-java-v1-osgi-1.11.766.jar`

### Note

The main file is the MANIFEST: it includes all Export packages of each AWS project. 

The Import packages are also defined. On your OSGI environment, if during the execution you get an exception of type NoClassDefFoundError or ClassNotFoundException, then it's probably a package missing in the import. Add it manually, then re-build re-deploy.
