# django-github-actions-aws
demonstrates how to set up a CI/CD Pipeline with GitHub Actions and AWS in a Django project

To help you get the big picture right, in summary, this is how our deployment setup is going to work: on push or pull request to main, GitHub Actions will test and upload our source code to Amazon S3. The code is then pulled from Amazon S3 to our Elastic Beanstalk environment. Picture the flow this way:

GitHub -> Amazon S3 -> Elastic Beanstalk
