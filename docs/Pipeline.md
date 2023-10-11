# CI/CD Pipeline

The CI/CD Pipeline is handled via CircleCI through three distinct steps.
1. Build
2. Hold
3. Deploy

![Pipeline](https://github.com/jeffreyricardo/udacity-full-stack-deploy/blob/main/screenshots/screenshot_circleci_build_success.png)

## Build
During the build step, all requisite code and libraries are retrieved and installed.  We then lint and build all frontend and backend code.
![Build Success](https://github.com/jeffreyricardo/udacity-full-stack-deploy/blob/main/screenshots/screenshot_circleci_build.png)

## Hold
Upon successful build, we then hold any deployments to AWS until appropriate approval is received
![Hold](https://github.com/jeffreyricardo/udacity-full-stack-deploy/blob/main/screenshots/screenshot_circleci_build_hold_deploy.png)

## Deploy
During this step, all code is deployed to their respective environments at AWS via EB CLI.
![Deploy](https://github.com/jeffreyricardo/udacity-full-stack-deploy/blob/main/screenshots/screenshot_circleci_deploy.png)