# Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React
4. 

## Installation
1. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`

# Deploy with Docker

## Requirements

1. Docker
2. Docker hub
3. Docker compose
4. Jenkins
5. AWS EC2

## Steps

1. clone code from git
2. build docker image
3. push image on docker hub
4. deploy on AWS 

![image](https://github.com/suryaadev/django-notes-app/assets/47253310/75f863f1-ba6f-47b7-b67c-4ca9ffa51855)
