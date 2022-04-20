# Running Automated Tests with Postman

This project is just a sample to showcase some end-to-end automated tests you can put in place with postman and newman.

You can completely ignore the java project in here, as it's here only to serve as a dummy application. 
To run this demo, use the dockerized version of the project or if you're a Java developer, just run it manually.


## The dummy application

This dummy app can be executed through docker with the following command:

```shell
docker run -d --name dummynewman -p 8080:8080 paulushc/devops-automation:v1.0.0
```

## Newman

### Simple

```
docker run -v $(pwd)/postman/:/etc/newman/ \
    --network host \
    -t postman/newman run collection.postman_collection.json
```

### With Environment

```
docker run -v $(pwd)/postman/:/etc/newman/ \
    --network host \
    -t postman/newman run collection.postman_collection.json \
    -e env.postman_environment.json
```

### Environment and Data

```
docker run -v $(pwd)/postman/:/etc/newman/ \
    --network host \
    -t postman/newman run collection.postman_collection.json \
    -e env.postman_environment.json \
    -d data.csv
```

### Environment and Data

```
docker run -v $(pwd)/postman/:/etc/newman/ \
    --network host \
    -t postman/newman run collection.postman_collection.json \
    -e env.postman_environment.json \
    -d data.csv \
    -r cli,json,junit
```

### Bailing

```
docker run -v $(pwd)/postman/:/etc/newman/ \
    --network host \
    -t postman/newman run collection.postman_collection.json \
    -e env.postman_environment.json \
    -d data.csv \
    -r cli,json,junit \
    --bail
```

