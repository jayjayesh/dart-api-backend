A server app built using [Shelf](https://pub.dev/packages/shelf),
configured to enable running with [Docker](https://www.docker.com/).

This sample code handles HTTP GET requests to `/` and `/echo/<message>`

# Running the sample

## Running with the Dart SDK

You can run the example with the [Dart SDK](https://dart.dev/get-dart)
like this:

```
$ dart run bin/server.dart
Server listening on port 8080
```

And then from a second terminal:
```
$ curl http://0.0.0.0:8080
Hello, World!
$ curl http://0.0.0.0:8080/echo/I_love_Dart
I_love_Dart
```

## Running with Docker

If you have [Docker Desktop](https://www.docker.com/get-started) installed, you
can build and run with the `docker` command:

```
$ docker build . -t myserver
$ docker run -it -p 8080:8080 myserver
Server listening on port 8080
```

And then from a second terminal:
```
$ curl http://0.0.0.0:8080
Hello, World!
$ curl http://0.0.0.0:8080/echo/I_love_Dart
I_love_Dart
```

You should see the logging printed in the first terminal:
```
2021-05-06T15:47:04.620417  0:00:00.000158 GET     [200] /
2021-05-06T15:47:08.392928  0:00:00.001216 GET     [200] /echo/I_love_Dart
```

## Stop : Any Running Docker Container
If you have updated api or added new api then docker container need to update with latest docker image file, here is how you do it.

```
$ docker ps
$ docker stop <container_name_or_id>
```

## Deploy API services
-- if you want to deploy this newly created APIs to globly, you can use docker_image to upload on google cloud 

OR

-- you could use [globe_cli](https://pub.dev/packages/globe_cli)

-- Note : globe login is not working on project IDX at the moment I've filed [an issue here](https://github.com/invertase/globe/issues/104) keep track it.

there is an update from globe contributor, lets follow his steps to deploy build.

```
(1) add your github project to their portal [Globe dashboard](https://globe.dev).
(2) while adding your github project, make sure you change entrypoint : by default it was (lib/main) but I have to change it to (bin/server.dart) for this project.
(2) get project_id : Globe dashboard > Project > Settings > Scroll Down to Project Id.
(3) generate token : Globe dashboard > Settings > Access Tokens.
(4) run this command into project idx terminal : globe deploy --project <your_project_id_from_dashboard> --token <your_access_token>
(5) here is how your api will look like :
    -- https://dart-api-backend-qsvirky-jayesh-lathiya.globeapp.dev
    -- https://dart-api-backend-qsvirky-jayesh-lathiya.globeapp.dev/hello/YourName
```


```
