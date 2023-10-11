# Hosting a Full-Stack Application

---

This project is the third and final project for the Udacity Full Stack JavaScript Developer Nanodegree.  The ojective is to demonstrate the deployment of an Angular application (with frontend and backend components) to AWS using CircleCI through a single CI/CD workflow.

The application can be accessed at the following URL:
http://udacity-udagram-20231010.s3-website-us-east-1.amazonaws.com


# Udagram

I elected to utilize the provided Udagram Starter Code as a basis for this project.  



### Dependencies

```
- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

```

### Project Setup

### AWS

A minimum set of AWS services are required for the successful operation of this application:
1. AWS RDS
2. AWS S3
3. AWS Elastic Beanstalk


### AWS RDS

RDS was configured using the following settings:
```
- Standard Create
- Engine: Postgres 13
- Template: Free tier
- Class: db.t3.micro
- Port: 5432
- DB Instance: udacity-full-stack-db
```
![RDS Configuration](https://github.com/jeffreyricardo/udacity-full-stack-deploy/blob/main/screenshots/screenshot_RDS.png)


### AWS S3

S3 was configured using the following settings:
```
- Bucket Name: udacity-udagram-20231010
- Object Ownership: ACLs Enabled, Bucket owner preferred to determine object access
- Block Public Access: NO, Create PUBLIC bucket
```
![S3 Configuration](https://github.com/jeffreyricardo/udacity-full-stack-deploy/blob/main/screenshots/screenshot_S3.png)


### AWS Elastic Beanstalk

EBS was configured via CLI using the following commands:
```
eb init
eb create --single --keyname udagram.pem --instance-types t2.medium

Environment Name: udagram-api-dev
DNS CNAME Prefix: udagram-api-dev
Spot Fleet: NO
Platform/Version: Node.js 18 running on 64bit Amazon Linux 2023/6.0.1
```
![Elastic Beanstalk](https://github.com/jeffreyricardo/udacity-full-stack-deploy/blob/main/screenshots/screenshot_ElasticBeanstalk.png)


## CircleCI

A prerequisite is the creation of a free CircleCI account.  Once logged in, a minimum set of steps was required to connect CircleCI Workspace to Github repo.

1. `cd starter/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End to End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework

## License

[License](LICENSE.txt)
