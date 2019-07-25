# ```aFrameWork```  - Application development and cloud deployment framework.



#### This is a framework repo for rapid application development using modern frameworks. This project includes following technologies grouped together for quick application development and deployment to Cloud environmnet.

  - React Application Framework ( https://github.com/react-boilerplate/react-boilerplate.git ), this framework provides CLI to generate custom react components as follows

    - Custom containers with following components pre build ( Basic Functionality included)

      - actions
      - constants
      - css
      - reducer
      - saga
      - selectors
      - index

    - CRUD functionality built and included as Containers and CLI 

      - CREATE
      - READ
      - UPDATE
      - DELETE

    - Search containers inclued in every container as an option in CLI.
    - Socket.io is included in each container for event broadcast and subscription.
  
  - MERN ( https://github.com/Hashnode/mern-starter.git ), which is currently depricated, but this project heavily modified the API environment to suit this framework.
    - AWS SDK is included and CLI is available for basic api code generation
    - API framework is built using promise and CLI auto code geneartion available with dummy data for mongo database.
  - GraphQL (Boilerplate GraphQL server with Apollo Server)
  - Serverless ( https://github.com/aws/aws-cdk.git ), For microservices development and deployment to cloud platform.
    - Express is used to manage the route for various Lambda function call
    - Serverless Offiline is included for offline lambda function testing.
  - AWS CDK ( https://github.com/aws/aws-cdk.git ), to develop AWS cloudformation template for resource deployment.
    - Build and deploy cloud formation template using typescript.




### Local Development folder structure

    .
    ├── app                         # React app for Frontend user interface
    ├── api                         # Nodejs API for scheduling and live event management 
    ├── graphql                     # GraphQL Playground using Apollo server
    ├── lambda                      # Lambda development environment with Serverless
    ├── cdk                         # Cloudformation development and deployment tool.
    ├── afreamework-cloudformation  # Cloud formation templates for deployment
    ├── docker                      # Docker compose and swarm files for ECS deployment in AWS
    ├── generator                   # Frontend and Backend code generation cli tool.
    ├── proxy                       # Nginx proxy for frontend application
    ├── LICENSE
    └── README.md


## Quick start

### Docker Local Development

```
$ cd docker
```

Update **.env** file with 

- *AWS_ACCESS_KEY_ID* 
- *AWS_SECRET_ACCESS_KEY*

Your AWS account will need to have appropriate **MediaLiveAccessRole** policy assigned.

#### Run

Run following command to build **app(react)** , **api(nodejs)**, **db(mongo:latest)**, **proxy(nginx)** docker images and start the containers

To Start Docker Containers run: 

```
$ docker-compose up
```

#### Stop
To stop the containers that are running, run:

```
$ docker-compose stop
```

#### Remove Docker Images from local device

To remove all images from local device run:

```
$ docker-compose down --rmi all
```

### Environment Details

Following directories of ```api``` mapped to development environment for local development


    volumes:
      - ../${API}/client:/usr/src/app/client
      - ../${API}/Intl:/usr/src/app/Intl
      - ../${API}/generators:/usr/src/app/generators
      - ../${API}/server:/usr/src/app/server
      - ../${API}/.babelrc:/usr/src/app/.babelrc
      - ../${API}/index.js:/usr/src/app/index.js
      - ../${API}/nodemon.json:/usr/src/app/nodemon.json
      - ../${API}/package.json:/usr/src/app/package.json
      - ../${API}/package-lock.json:/usr/src/app/package-lock.json
      - ../${API}/webpack.config.babel.js:/usr/src/app/webpack.config.babel.js
      - ../${API}/webpack.config.dev.js:/usr/src/app/webpack.config.dev.js
      - ../${API}/webpack.config.prod.js:/usr/src/app/webpack.config.prod.js
      - ../${API}/webpack.config.server.js:/usr/src/app/webpack.config.server.js


Following directories of ```app``` mapped to development environment for local development


    volumes:
      - ../${APP}/app:/app/app
      - ../${APP}/internals:/app/internals

Following directories of ```lambda``` mapped to development environment for local development


    volumes:
      - ../${LAMBDA}/src:/lambda/src
      - ../${LAMBDA}/serverless.yml:/lambda/serverless.yml
      - ../${LAMBDA}/package.json:/lambda/package.json

Following directories of ```graphql``` mapped to development environment for local development


    volumes:
      - ../${GRAPHQL}/src:/graphql/src
      - ../${GRAPHQL}/package.json:/graphql/package.json

Instructions and commands for ```cdk```  app for build and deploy from CLI


    Global CLI Install:
      $ npm i -g aws-cdk
    
    Install Local Packages:
      $ npm install
    
    Build: 
      $ npm run build
    
    Watch:
      $ npm run watch
    
    CDK Commands:

      Synth Cloudformation Template:

      $ cdk synth --app='node bin/main.js' --output=templates
      
      Diff stacks against current state:

      $ cdk diff --app='node bin/main.js' MyStackName --template=path/to/template.yml

      cdk deploy:

      $ cdk deploy --app='node bin/main.js' MyStackName --profile "aws profile name"

      cdk destroy

      $ cdk destroy --app='node bin/main.js' MyStackName --profile "aws profile name"


Instructions and commands for ```lambda``` app in local development environment


    Global CLI Install:
      $ npm i -g serverless

    Setup AWS Profile

      - provider:
         - name: aws
         - runtime: nodejs8.10
         - profile: femasters
         - region: ap-southeast-2
         - stage: dev

    Deploy a Service:

      serverless deploy -v
    
    Deploy the Function:

      serverless deploy function -f hello
    
    Invoke the Function on AWS:

      serverless invoke -f hello -l

    Invoke the Function on your machine:

      serverless invoke local -f hello -l

    Fetch the Function Logs:

      serverless logs -f hello -t
    
    Remove the Service:

      serverless remove







```dbdata``` volume will be mapped to ```/data/db``` for mongodb document storage


### Access URL and Port Mapping


   * PROXY_URL: [http://localhost](http://localhost)
   * APP_URL: [http://localhost:3000](http://localhost:3000)
   * MONGO_URL: [mongodb://localhost:27018/api]([mongodb://localhost:27018/api])
   * API_URL: [http://localhost:8080/api/{model}](http://localhost:8080/api/{model})
   * AWS_API_URL: [http://localhost:8080/api/aws/{model}](http://localhost:8080/api/aws/{model})
   * LAMBDA_URL: [http://localhost:3500/](http://localhost:3500/)
   * GRAPHQL_URL: [http://localhost:3001/](http://localhost:3001/)
   * GRAPHQL_MONGO_URL: [mongodb://localhost:27018/api-design](mongodb://localhost:27018/api-design)
