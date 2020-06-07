# JAMES WARD SUBMISSION DETAILS
1. Github Repo: https://github.com/jw-gitgo/udagramrefactorproject
2. Dockerhub Repos:
    - https://hub.docker.com/repository/docker/jmrwnd/udacity-frontend
    - https://hub.docker.com/repository/docker/jmrwnd/udacity-restapi-feed
    - https://hub.docker.com/repository/docker/jmrwnd/udacity-restapi-user
    - https://hub.docker.com/repository/docker/jmrwnd/reverseproxy
3. Screenshots requested:
    - TravisCIBuildSucceeded.jpg: shows Travis CI build successfully completing without errors
    - KubectlShowsRunningK8sPods.jpg: Screenshot of kubectl get pod which shows all running containers (I only launched one of each due to resource constraints)
    - UdagramSuccessfullyRunning.jpg: Shows the udagram application successfully running on Kubernetes
    - K8sClusterRUnningOnAWS.jpg: shows Kubernetes cluster successfully deployed in AWS using Kops
    - UdagramRunningOnK8sClusterInAWS.jpg: shows the Udagram application running on the AWS Kubernetes cluster
    - K8sABRollingDeployment.jpg: shows a new docker image being applied to a deployment, and the rolling update bringing it up in an A/B fashion, so that services are not interrupted.
4. CI/CD Deployment:
    - NOTE: I was instructed in the mentor forums that I do not need to set up automatic deployment to Kubernetes through Travis CI to complete this project:
        - https://knowledge.udacity.com/questions/107660 
        - https://knowledge.udacity.com/questions/163181
    - I stood up a Kubernetes cluster in AWS using kops, and I know that I would need to add the kubernetes deploy scripts in the .travis.yml file, and I would need to add the appropriate environment variables in Travis CI as well.
    - While I understand in theory how to do this, I stopped after I got a successful docker-compose build in Travis CI, since the mentor forums say the next steps are beyond the scope of this course.
5. A/B Testing Requirement:
    - Per this mentor forum post, I achieved this by doing a rolling update of the kubernetes cluster:
        - https://knowledge.udacity.com/questions/111811

FEEDBACK: this course (both the old version and the new version) and project have been very disappointing. The course and project instructions are often very unclear, many steps and key information are missing, and this causes students to have to do hours (or days) of troubleshooting to complete even the most basic steps. I did the Data Analyst nanodegree several years ago, and the quality of the course and projects was much better. It is a shame that this course (and particularly this project) do not seem to be nearly as well-executed. On the positive side, Juan and Emil have been outstanding at quickly and thoroughly answering questions in the Mentor Forums - without their help, it would not be possible to complete this course at all.

# --------------ORIGINAL README BELOW----------------------

# Udagram Image Filtering Microservice

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.

The project is split into three parts:
1. [The Simple Frontend](/udacity-c3-frontend)
A basic Ionic client web application which consumes the RestAPI Backend. 
2. [The RestAPI Feed Backend](/udacity-c3-restapi-feed), a Node-Express feed microservice.
3. [The RestAPI User Backend](/udacity-c3-restapi-user), a Node-Express user microservice.

## Getting Setup

> _tip_: this frontend is designed to work with the RestAPI backends). It is recommended you stand up the backend first, test using Postman, and then the frontend should integrate.

### Installing Node and NPM
This project depends on Nodejs and Node Package Manager (NPM). Before continuing, you must download and install Node (NPM is included) from [https://nodejs.com/en/download](https://nodejs.org/en/download/).

### Installing Ionic Cli
The Ionic Command Line Interface is required to serve and build the frontend. Instructions for installing the CLI can be found in the [Ionic Framework Docs](https://ionicframework.com/docs/installation/cli).

### Installing project dependencies

This project uses NPM to manage software dependencies. NPM Relies on the package.json file located in the root of this repository. After cloning, open your terminal and run:
```bash
npm install
```
>_tip_: **npm i** is shorthand for **npm install**

### Setup Backend Node Environment
You'll need to create a new node server. Open a new terminal within the project directory and run:
1. Initialize a new project: `npm init`
2. Install express: `npm i express --save`
3. Install typescript dependencies: `npm i ts-node-dev tslint typescript  @types/bluebird @types/express @types/node --save-dev`
4. Look at the `package.json` file from the RestAPI repo and copy the `scripts` block into the auto-generated `package.json` in this project. This will allow you to use shorthand commands like `npm run dev`


### Configure The Backend Endpoint
Ionic uses enviornment files located in `./src/enviornments/enviornment.*.ts` to load configuration variables at runtime. By default `environment.ts` is used for development and `enviornment.prod.ts` is used for produciton. The `apiHost` variable should be set to your server url either locally or in the cloud.

***
### Running the Development Server
Ionic CLI provides an easy to use development server to run and autoreload the frontend. This allows you to make quick changes and see them in real time in your browser. To run the development server, open terminal and run:

```bash
ionic serve
```

### Building the Static Frontend Files
Ionic CLI can build the frontend into static HTML/CSS/JavaScript files. These files can be uploaded to a host to be consumed by users on the web. Build artifacts are located in `./www`. To build from source, open terminal and run:
```bash
ionic build
```
***