# django-github-actions-aws
demonstrates how to set up a CI/CD Pipeline with GitHub Actions and AWS in a Django project

To help you get the big picture right, in summary, this is how our deployment setup is going to work: on push or pull request to main, GitHub Actions will test and upload our source code to Amazon S3. The code is then pulled from Amazon S3 to our Elastic Beanstalk environment. Picture the flow this way:

GitHub -> Amazon S3 -> Elastic Beanstalk

The only other way we could upload code directly to an Elastic Beanstalk instance with our current setup, is if we were using the AWS Elastic Beanstalk CLI (EB CLI).

Using the EB CLI requires running some shell command that would then require that we respond with some input.

Now, if we are deploying from our local machine to Elastic Beanstalk, when we run the EB CLI commands, we'd be there to type in the required responses. But with our current setup, those commands would be executed on GitHub Runners. We wouldn't be there to provide the required responses. The EB CLI isn't the easiest deployment tool for our use case.

With the approach we've picked, we'd run a shell command that uploads our code to S3 and then another command that pulls the uploaded code to our Elastic Beanstalk instance. These commands, when run, do not require that we submit some responses. Having the Amazon s3 step is the easiest way to go about this.
