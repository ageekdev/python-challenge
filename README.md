# Python take-home challenge

In this challenge, you will build a python application server for machine learning system by using our toy Machine Learning server api.

## Requirements

### Prediction end point.

* This end point will accept base64 image and return the prediction result of machine learning server api.
* Basic Authentication for the end point must be provided.
* Input Image and result for the input must be logged in database. You can save image on file system or google cloud and only store reference on database and stored image must be encrypted.
* Dockerize the application server.

### Hosting

* Please use your own Digital Ocean or AWS servers to do the deployment and url for us to test.
* If you have trouble getting a working DO / AWS accounts, let us know in advance.

## Resource

* Machine Learning Server Api: <https://hub.docker.com/repository/docker/yyhtoon/mnet-serving>


    ### Instructions for Machine Learning Server Api.

    * You will need to run our toy machine learning server on your machine using docker.
        ```
        docker run -p 8501:8501 yyhtoon/mnet-serving
        ```
    * Then, rest api to the toy server will be available at http://localhost:8501/v1/models/mnet:predict.
    * Api accept image in base64 string.
    * Payload example
        ```
        {"instances":[base64_img_str]}
        ```
    * Payload in Python code example
        ```
        with open("example.jpeg","rb") as data:
            img_data = data.read()
        img_data = base64.urlsafe_b64encode(img_data)
        data = {"instances":[img_data.decode('utf-8')]}
        ```
    * Response
        ```
        {'predictions': [332]}
        ```
## Note

* We suggest you to use fastapi framework if you feel confortable with it.
* For better impression, you are not limited to implement followings in the project:
    * Monitoring of api service
    * Logging input/ouputs
    * Performance oriented server setups / configuration
    * Good choice of Database