
# Tensorflow image classification

> [!TIP]
> To deploy this project using **GUI-based flow**, navigate to [console](https://console.stacktape.com/create-new-project/git-project-using-console?name=my-stacktape-app&repositoryType=public&repositoryUrl=https://github.com/stacktape/starter-tensorflow-image-classification)

- Example Docker container deployed as a [web service](https://docs.stacktape.com/compute-resources/web-services/).
- This project includes a pre-configured [stacktape.yml configuration](stacktape.yml).
The configured infrastructure is described in the [stack description section](#stack-description)

## Pricing


- The infrastructure required for this application uses exclusively "serverless", pay-per-use infrastructure. If your load won't get high, these costs will be close to $0.

## Prerequisites

1. **AWS account**. If you don't have one, [create new account here](https://portal.aws.amazon.com/billing/signup).

2. **Stacktape account**. If you don't have one, [create new account here](https://console.stacktape.com/sign-up).

3. **Stacktape installed**.

  <details>
  <summary>Install on Windows (Powershell)</summary>

  ```bash
  iwr https://installs.stacktape.com/windows.ps1 -useb | iex
  ```

  </details>
  <details>
  <summary>Install on Linux</summary>

  ```bash
  curl -L https://installs.stacktape.com/linux.sh | sh
  ```

  </details>
  <details>
  <summary>Install on MacOS</summary>

  ```bash
  curl -L https://installs.stacktape.com/macos.sh | sh
  ```

  </details>
  <details>
  <summary>Install on MacOS ARM (Apple silicon)</summary>

  ```bash
  curl -L https://installs.stacktape.com/macos-arm.sh | sh
  ```

  </details>




## 1. Generate your project
To initialize the project, use

```bash
stacktape init --starterId tensorflow-image-classification
```

## 2. Before deploy
 - Install your projects dependencies. The recommended way is to use [Virtual environment](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/).

## 3. Deploy your stack

The deployment will take ~5-15 minutes. Subsequent deploys will be significantly faster.

<details>
<summary>Deploy from local machine</summary>

<br />

The deployment from local machine will build and deploy the application from your system. This means you also need to have:
- Docker. To install Docker on your system, you can follow [this guide](https://docs.docker.com/get-docker/).- [Python version > 3.9](https://www.python.org/) and [Poetry](https://python-poetry.org/docs/) package manager installed.

<br />

To perform the deployment, use the following command:

```bash
stacktape deploy --projectName <<project-name>> --stage <<stage>> --region <<region>>
```

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using AWS CodeBuild pipeline</summary>

<br />

Deployment using AWS CodeBuild will build and deploy your application inside [AWS CodeBuild pipeline](https://aws.amazon.com/codebuild/). To perform the deployment, use

```bash
stacktape codebuild:deploy --stage <<stage>> --region <<region>> --projectName <<project-name>>
```

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using Github actions CI/CD pipeline</summary>

<br />

1. If you don't have one, create a new repository at https://github.com/new
2. Create Github repository secrets: https://docs.stacktape.com/user-guides/ci-cd/#2-create-github-repository-secrets
3. Replace `<<stage>>` and `<<region>>` in the .github/workflows/deploy.yml file.
4. `git init --initial-branch=main`
5. `git add .`
6. `git commit -m "setup stacktape project"`
7. `git remote add origin git@github.com:<<namespace-name>>/<<repo-name>>.git`
8. `git push -u origin main`
9. To monitor the deployment progress, navigate to your github project and select the Actions tab

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using Gitlab CI pipeline</summary>

<br />

1. If you don't have one, create a new repository at https://gitlab.com/projects/new
2. Create Gitlab repository secrets: https://docs.stacktape.com/user-guides/ci-cd/#2-create-gitlab-repository-secrets
3. replace `<<stage>>` and `<<region>>` in the .gitlab-ci.yml file.
4. `git init --initial-branch=main`
5. `git add .`
6. `git commit -m "setup stacktape project"`
7. `git remote add origin git@gitlab.com:<<namespace-name>>/<<repo-name>>.git`
8. `git push -u origin main`
9. `To monitor the deployment progress, navigate to your gitlab project and select CI/CD->jobs`

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>

## 4. Test your application

After a successful deployment, some information about the stack will be printed to the terminal (**URLs** of the deployed services, links to **logs**, **metrics**, etc.).

- Explore your application at **app URL**. The URL is printed to the terminal.





## 5. Hotswap deploys
- Stacktape deployments use [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) under the hood. It
  brings a lot of guarantees and convenience, but can be slow for certain use-cases.

- To speed up the deployment, you can use the `--hotSwap` flag which avoids using Cloudformation.
- Hotswap deployments work only for source code changes (for lambda function, containers and batch jobs) and for content uploads to buckets.
- If the update deployment is not hot-swappable, Stacktape will automatically fall back to using a Cloudformation deployment.
```bash
stacktape deploy --hotSwap --stage <<stage>> --region <<region>> --projectName <<project-name>>
```

## 6. Delete your stack

- If you no longer want to use your stack, you can delete it.
- Stacktape will automatically delete every infrastructure resource and deployment artifact associated with your stack.

```bash
stacktape delete --stage <<stage>> --region <<region>>
```

# Stack description

  Stacktape uses a simple `stacktape.yml` configuration file to describe infrastructure resources, packaging, deployment
  pipeline and other aspects of your project.

  You can deploy your project to multiple environments (stages) - for
  example `production`, `staging` or `dev-john`. A stack is a running instance of an project. It consists of your application
  code (if any) and the infrastructure resources required to run it.

  The configuration for this project is described below.

  ## 1. Resources

  - Every resource must have an arbitrary, alphanumeric name (A-z0-9).
  - Stacktape resources consist of multiple underlying AWS or 3rd party resources.
### 1.1 Buckets

Buckets offer persistent, scalable storage for any type of object(files).

In this project we use two buckets:

- **inputBucket** - used for uploading `.zip` file(s) containing pictures that we wish to classify(categorize)
- **outputBucket** - used by apps batch job to output images categorized into classes.

You can configure [multiple properties](https://docs.stacktape.com/resources/buckets/) on the bucket. In this case, we
are using the default setup.

```yml
inputBucket:
  type: bucket

outputBucket:
  type: bucket
```

### 1.2 Batch job

The classifier application runs in a batch job.

The batch job is configured as follows:

- [Container](https://docs.stacktape.com/compute-resources/batch-jobs/#container) section specifies details of our job
  container
  - **Packaging** - determines how the Docker container image is built. In this example, we are using our custom
    `Dockerfile` based of [tensorflow image](https://hub.docker.com/r/tensorflow/tensorflow/). Stacktape builds the
    Docker image and pushes it to a pre-created image repository on AWS. You can also use
    [other types of packaging](https://docs.stacktape.com/configuration/packaging/#packaging-multi-container-workloads).
- **ConnectTo list** - we are adding buckets `inputBucket` and `outputBucket` into `connectTo` list. By doing this,
  Stacktape will automatically setup necessary IAM permissions for the batch job's role as well as inject relevant
  environment variables into the runtime (such as AWS names of the buckets).
- [Resources](https://docs.stacktape.com/compute-resources/batch-jobs/) assigned to the job. We are providing the number
  of cpus and the amount of memory the job needs. When job is triggered AWS will automatically spin-up an instance with
  the required resources on which the job will run. We are also using the `useSpotInstances` property, which configures
  job to use cheaper [spot instances](https://docs.stacktape.com/compute-resources/batch-jobs/#spot-instances).
- [Access control](https://docs.stacktape.com/compute-resources/batch-jobs/#accessing-other-resources) - Since our job
  reads from `inputBucket` and writes to `outputBucket`, it needs permissions to access these resources. We are granting
  the permissions by listing them in `connectTo` list. To see other ways of controlling access to resources refer to
  [the docs](https://docs.stacktape.com/compute-resources/batch-jobs/#accessing-other-resources)
- We are configuring **events** that trigger the job. In this case, we are triggering the batch job if a `zip` file is
  uploaded to (created in) the `inputBucket`.

```yml
classifierJob:
  type: batch-job
  properties:
    container:
      packaging:
        type: custom-dockerfile
        properties:
          buildContextPath: ./
    resources:
      cpu: 2
      memory: 14000
    useSpotInstances: true
    connectTo:
      - inputBucket
      - outputBucket
    events:
      - type: s3
        properties:
          bucketArn: $ResourceParam('inputBucket', 'arn')
          s3EventType: s3:ObjectCreated:*
          filterRule:
            suffix: .zip
```
