## Identify Competencies
* How many Services do we need?
  
  * Stream back end
  * front end
  * Auth

## Technical Requirements
* golang main lang
* rtmp streaming
* gRPC APIs
* Docker images (Auto Build CI)
* Documentation in Repo; in Code; GoDoc?
* TLS secured
* Kubernetes compatible
* Authentication /enable/disable

## Features/Requirements
### Back end
* Consumes RTMP streams from f.e. OBS
* Multiple streamer clients
* Multiple bitrate decoding
* Dash and HLS streams possible
* Independent scalable
* possibility for streaming secret (Auth)
* can record a stream if wanted
* can stream VOD
* Stream statistics

### Front end
* Plays RTMP stream from back end
* Can be configured to ask for a password on entrance   
  * Per stream !?
* Shows all connected streamers
* Allows changing to a different streamer
* Allows changing of stream quality (Bitrate)
* Allows changing technology from dash to hls and vice versa
  
  * Auto detect client and change technology for that client; but still allow manual change
* Independent scalable

## MVP
Deployment in Docker images
Discovery:

* gRPC (protobuf) [PacktPub eBook Repo](https://github.com/PacktPublishing/-gRPC-Golang-Master-Class-Build-Modern-API-and-Microservices) |
  [reference Go implementaion repo](https://github.com/grpc/grpc-go)

### Back end
* publishes at least one streamer

Endpoint for incoming rtmp stream
Exposing endpoint for dash fragments
Discovery:

* Convert rtmp in dash fragments in go
* pushes meta data (Stream goes online) to frontend (directly, events)

### Front end
* Users can consume published stream from back end
* Volume control (mute, unmute, louder, quieter)
* pause/unpause
* Full screen mode
  Discovery:
  
  * pulls Meta data from back end (Stream goes online)

### Auth
* Will be postponed
