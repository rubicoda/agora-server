# Agora Server for Cloud Recording and Real Time Transcription


<a target="_blank" href="https://render.com/deploy?repo=https://github.com/AgoraIO-Community/agora-server">
  <img src="https://render.com/images/deploy-to-render-button.svg" alt="Deploy to Render">
</a>

## Getting Started

```
pip install flask
```

## Create a `.env` file with the following values
```
CUSTOMER_KEY = "<--Agora Customer Key-->"
CUSTOMER_SECRET = "<--Agora Customer Secret-->"

TEMP_TOKEN = "<--Agora Temporary Token-->"
APP_ID = "<--Agora App ID-->"

SECRET_KEY = "<--Cloud Service Secret Key-->"
ACCESS_KEY = "<--Cloud Service Access Key-->"
BUCKET_NAME = "<--Cloud Service Bucket Name-->"
```

You can learn about creating your Customer Key and Secret [here](https://docs.agora.io/en/video-calling/reference/manage-agora-account?platform=flutter#generate-a-customer-id-and-customer-secret)

## Starting Server

```
python -m flask run 
```

## Interfaces

### Start Cloud Recording
#### Endpoint
```
/start-recording/<--Channel Name-->
```
#### Successful Response
```
{sid: <--SID Value-->, resource_id: <--Resource ID Value-->}
```

### Stop Cloud Recording
#### Endpoint
```
/stop-recording/<--Channel Name-->/<--SID-->/<--Resource ID-->
```

### Start Real Time Transcription
#### Endpoint
```
/start-transcribing/<--Channel Name-->
```
#### Successful Response
```
{taskId: <--Task ID Value-->, builderToken: <--Builder Token Value-->}
```

### Stop Real Time Transcription
#### Endpoint
```
/start-transcribing/<--Channel Name-->/<--Task ID-->/<--Builder Token-->
```

#### How it works?
Once you have the server working properly, within your application you can access the generated text using the `onStreamMessage`. This will come in random numbers, but you can decipher what that means using [Google Protocol Buffers](https://protobuf.dev)
