# eb-java elastic beanstalk with JAVA application

This repository shows a minimum example of how to use JAVA spring boot with AWS elastic beanstalk. Many of ideas in this repo are from the [aws-samples/eb-java-scorekeep](https://github.com/aws-samples/eb-java-scorekeep). 

There are some reasons why I decide to create this repo. 

The scorekeep repo has much information. However, it is an application example. It takes me a while to figure out the elastic beanstalk settings from the repo. I would like to present a hello world style example for people who deploy their java app to AWS elastic beanstalk first time. It might be helpful for them if there is a boilerplate. 

This example is managed by the [Gradle build tool](https://gradle.org/). All the settings are in the file `build.gradle`.

Here is one thing you should know; This project is using gradle `2.7`. 

The reason why I use the version `2.7` is that I can not to deploy my app successfully at first because the default Gradle version on the elastic beanstalk machine is using `2.7`.

I try to upgrade the Gradle version on the machine in the hack way, but this fails when the auto-scaling. The settings could not be brought to the new instance when the auto-scaling happens. 

Because of the Gradle version is old, the spring boot version is forced to use the `1.4` version. 

I hope AWS can upgrade the java platform someday then developers can use the up-to-date version of the Gradle and the Spring boot.

# Usage:

## Development

As long as you have the same structure of this repo, running up this app is easy. 

Simply run these commands:

```
./gradlew build
java -jar build/libs/eb-java-0.0.1-SNAPSHOT.war
```

If you are using an IDE, such as IntelliJ or Eclipse, it is much easier they help you resolve everything.  You can run the application by clicking the run button. 

## Deployment

If your application run everything smoothly on your local machine, there is only one command to run for the deployment. 

Before you deploy your app, I would suggest you check all the environmental variables are set correctly on the elastic beanstalk. You can also specify those variables in the file, `.ebextensions/01_env_var.config`.

Then you can run the `eb` command:

```
eb deploy
```

# MISC

If you meet any problem while using this repo, please leave your question by creating a new issue! 

I am also welcome to any pull request that improves this project. 

Thank you!


