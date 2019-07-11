# Social Media Live Stream Management Interface.



#### This is the repo for Social Media Stream management. This interface allows MCR to manage live event booking, stream control, encoding and distribution from a web interface.

This application will have social stream booking system, which will enable MCR to create booking events, automate the stream distribution, RTP/RTMP/UDP stream broadcasting for live events on demand.

Broadcasting team will have access to all encoding resources, input, channel management, distribution control of the broadcast media via media package, or direct RTMP/RTMPS push to facebook, youtube or any other social media platforms.


### Local Development folder structure

    .
    ├── app                   # React app for Frontend user interface
    ├── api                   # Nodejs API for scheduling and live event management 
    ├── cdk                   # Cloud formation development repo
    ├── cloudformation        # Cloud formation templates for deployment
    ├── docker                # Docker files for ECS deployment
    ├── proxy                 # Nginx proxy for frontend application
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
      - ../api/client:/usr/src/app/client
      - ../api/Intl:/usr/src/app/Intl
      - ../api/generators:/usr/src/app/generators
      - ../api/server:/usr/src/app/server
      - ../api/.babelrc:/usr/src/app/.babelrc
      - ../api/index.js:/usr/src/app/index.js
      - ../api/nodemon.json:/usr/src/app/nodemon.json
      - ../api/package.json:/usr/src/app/package.json
      - ../api/package-lock.json:/usr/src/app/package-lock.json
      - ../api/webpack.config.babel.js:/usr/src/app/webpack.config.babel.js
      - ../api/webpack.config.dev.js:/usr/src/app/webpack.config.dev.js
      - ../api/webpack.config.prod.js:/usr/src/app/webpack.config.prod.js
      - ../api/webpack.config.server.js:/usr/src/app/webpack.config.server.js


Following directories of ```app``` mapped to development environment for local development


    volumes:
      - ../app/app:/app/app
      - ../app/internals:/app/internals


```dbdata``` volume will be mapped to ```/data/db``` for mongodb document storage


### Access URL and Port Mapping


   * APP_URL: [http://localhost:3000](http://localhost:3000)
   * MONGO_URL: [mongodb://localhost:27018/api]([mongodb://localhost:27018/api])
   * API_URL: [http://localhost:8080/api/{model}](http://localhost:8080/api/{model})
   * AWS_API_URL: [http://localhost:8080/api/aws/{model}](http://localhost:8080/api/aws/{model})
   * PROXY_URL: [http://localhost](http://localhost)
