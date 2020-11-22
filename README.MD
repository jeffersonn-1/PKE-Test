# PKE Test

### Clone application:

```sh
$ git clone git@github.com:jeffersonn-1/pke-test.git
$ cd pke-test
$ git checkout master
```

### Install dependencies with one command (all required installation is included in `build.sh` file):

```sh
$ npm run build
```

This will install all dependencies including Serverless and it's plugins for deploy.

### To deploy your code to AWS resources using Serverless which was installed on previous stage:

```sh
$ sls config credentials --provider aws --key 1234 --secret 5678
$ sls deploy
```

Upon successfull deployment you will get two HTTP endpoints as follows:

- Gets signed url for uploading mp3 file. The name of the file is generated using \${new Date().getTime()} function so to upload file using that URL you will have to name the file accordingly as returned in URL. The Expiration time is set to 120s.

```sh
/upload-url
```

Using returned URL it is possible to upload .mp3 file to the S3 bucket.

- Next, to get the signed urls for all songs which has been uploaded and trimmed use the following route:

```sh
/songs
```

This will return signed urls to download cropped songs to 5 seconds using FFMPEG.

You can find a Postman collection with the link below:

> https://www.getpostman.com/collections/d7c3b15aae1b4270bbb3

### To run tests use the following command

```sh
$ npm run test
```

In watch mode use

```sh
$ npm run test:watch
```
